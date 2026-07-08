# NagpurLens — Success Metrics

> **Authors:** Mohammad Ammar · Zahid Khan · Mohammad Ruwaifa
> **Document Status:** Foundational — derived from `VISION.md` and `PROBLEM.md`. Defines what success means, not what the roadmap contains.
> **Version:** v1.2
> **Last Updated:** July 2026
> **Revision History:** v1.0 (July 2026) — initial draft. v1.1 (July 2026) — consolidated the vanity-metrics exclusion (previously stated three times) into a single canonical statement in Section 0; added explicit verification mechanisms to the highest-ambiguity metrics; added Section 17, "Open Items," flagging the KPI-set gap inherited from `VISION.md`/`PROBLEM.md`. v1.2 (July 2026) — KPI-set gap resolved upstream in `VISION.md` v1.1 and `PROBLEM.md` v1.1; Section 7 updated to include HAS and MII as v1.0 KPIs; Section 17 removed.

---

## 0. Purpose and Scope

This document defines success. It is not a roadmap — `VISION.md` Section 8 already defines the versioned roadmap — and it is not a task list. Its purpose is to state, for each dimension of the project, what a passing outcome looks like, in terms that can be checked rather than argued about.

Two constraints govern every metric in this document. First, every metric must be measurable — either it passes or it does not, or it produces a number that can be compared against a stated threshold, and the check that produces that pass/fail must be named, not implied. Second, no metric in this document is a vanity metric. **GitHub stars, forks, likes, follower counts, and similar engagement figures are excluded from every dimension of success defined below** — they measure attention, not engineering quality, and `VISION.md` Section 5 is explicit that the real product is the validated, documented, reproducible data platform, not its popularity. This exclusion applies uniformly to Sections 9 (Community) and 10 (Open Source); those sections do not restate it.

Where a metric differs by version, this document states the Version 1, Version 2, Version 3, and Version 4 threshold separately. A metric with no version distinction applies uniformly across all versions from the point it is introduced.

---

## 1. Mission Success

Mission success is measured against the three questions defined in `three_questions.md`, not against feature count.

| Metric | Threshold |
|---|---|
| Questions answered with a validated, auditable score | 1 of 3 by v1.0; 2 of 3 by v2.0; 3 of 3 by v3.0 |
| Public claims traceable to documented evidence | 100% — every claim in dashboard, website, or README has a traceable source or stated assumption |
| Instances of undisclosed data limitation | 0 — per `VISION.md` Section 7.4, every limitation is stated in the relevant output, not omitted |

---

## 2. Engineering Success

| Metric | Threshold | Verification Mechanism |
|---|---|---|
| CI pipeline (GitHub Actions) passing on `main` | 100% of merged commits | GitHub Actions status check, required for merge |
| Automated unit tests covering schema constraints, KPI computation, and API responses | Present from v1.0 onward; test count grows with each version's new components | Test suite run in CI; coverage report attached to each release |
| Build reproducibility: a contributor with no prior context can rebuild the full database from the repository alone | Verified true, per `VISION.md` Section 7.3 | A named external reviewer (not a core team member) performs a clean clone-to-database rebuild before each version is tagged, and records the result in `validation_report.md` |
| Undocumented manual steps required to reproduce the pipeline | 0 | Same clean-environment rebuild above; any manual step discovered is either automated or documented before release |

---

## 3. Database Success

| Metric | v1.0 Threshold |
|---|---|
| Localities in database | 50+ |
| Infrastructure records | 150+ |
| Orphan infrastructure records (no valid locality_id) | 0 |
| Foreign key constraints enforced at the schema level | 100% of relational links |
| Locality ID standard consistency (`XXX` format) across every table | 100% |

For Version 2 and beyond, this section extends to whatever new tables are introduced (construction activity, growth signals, price data), applying the same zero-orphan, fully-constrained standard.

---

## 4. Data Quality Success

| Metric | Threshold |
|---|---|
| Records with a named, dated source in the source registry | 100% |
| GPS coordinates validated against an independent geographic reference | 100% of localities |
| Infrastructure-to-locality assignments verified by haversine nearest-centroid check | 100%, zero orphan records |
| Validation report checks passing (null checks, GPS bounds, join integrity) | 100% PASS at time of each release |
| Data quality limitations explicitly documented (e.g., Census 2011 age) | Stated in every relevant output — not a pass/fail metric, but a mandatory disclosure |

---

## 5. Research Success

| Metric | Threshold |
|---|---|
| Dataset citable by an external researcher without contacting the team | True from v1.0 — achieved via source registry, methodology document, and open license |
| Methodology decisions with a documented evidentiary basis | 100% |
| Independent reproducibility of a published KPI value from raw source data | Verified for at least one KPI per version, by someone outside the core team where feasible; the specific KPI checked and the reviewer's identity are recorded in `validation_report.md` |

Research success is not measured by citation count or academic adoption at this stage — those are outcomes the platform may eventually produce, but they are not within NagpurLens's control and are therefore not used as success criteria.

---

## 6. Documentation Success

| Metric | Threshold |
|---|---|
| Repository files with a stated document status and traceability to `VISION.md` | 100% of foundational documents (`PROBLEM.md`, `data_dictionary.md`, `source_registry.md`, `kpi_definitions.md`, `validation_report.md`, `methodology.md`) |
| README leads with a real, numbered finding from actual data | True, per `VISION.md` Section 5 and Section 10 |
| Undocumented assumptions discovered during external review | 0 |

---

## 7. Analytics Success

| Metric | v1.0 | v2.0 | v3.0 |
|---|---|---|---|
| KPIs defined, formula-public, and version-controlled | IDI, PIR, HAS, MII | + GSI | + IAS |
| KPI values reproducible from raw data by an external party | Required | Required | Required |
| KPI methodology changes documented with revision history | Required from first introduction of each KPI onward | | |

HAS and MII are delivered alongside IDI and PIR at v1.0 because both are computable directly from the Version 1 infrastructure table, with no dependency on Version 2 or 3 data — consistent with `VISION.md` Section 4's version-tagged KPI list.

---

## 8. Product Success

| Metric | Threshold |
|---|---|
| Dashboard publicly accessible | Live at v1.0 (`PROBLEM.md` Section 8) |
| REST API endpoints live and documented | `/localities`, `/infra`, `/gap-analysis` at v1.0; extended per later versions |
| Dashboard and API reflect the same underlying validated data (no drift) | 100% consistency, checked at release time |
| Public website live | At v1.0 |

Product success at this stage is measured by correctness and availability of the product surface, not by usage volume. Usage-based success criteria are appropriate once the platform reaches Version 4 (see Section 13, which builds on this section's release criteria rather than duplicating them).

---

## 9. Community Success

Community success is measured by the quality of contribution infrastructure, not by contributor count or social engagement (see Section 0).

| Metric | Threshold |
|---|---|
| Contribution guide present and accurate | Present from v1.0 |
| External contributor able to set up the full pipeline using only repository documentation | Verified by the same clean-environment rebuild process described in Section 2, performed by someone outside the core team |
| Issues and pull requests responded to with a substantive engineering comment | Applies once the repository accepts external contributions; not a v1.0 requirement given project stage |

---

## 10. Open Source Success

| Metric | Threshold |
|---|---|
| License present and applied consistently across code and data | Required from v1.0 |
| Data provenance and reuse terms documented for every dataset | 100% |
| Repository buildable and auditable by a party with zero prior contact with the team | Verified, per `VISION.md` Section 7.3, using the same rebuild process as Section 2 |

---

## 11. Governance Success

| Metric | Threshold |
|---|---|
| Every scope decision traceable to Section 3, 6, 7, or 8 of `VISION.md` | 100%; anything untraceable is scope creep per `VISION.md` Section 13 |
| Version boundaries respected (no Version 2 feature merged before Version 1 validation is complete) | 100%, per `VISION.md` Section 7.6 |
| Document status headers kept current when a foundational document changes | 100% |
| Cross-document contradictions discovered during review are tracked to resolution, not silently worked around | 100% — see `VISION.md`'s and `PROBLEM.md`'s v1.1 revision histories for the standing example of this process in practice |

---

## 12. Long-Term Success

Long-term success is evaluated at the platform level, not the Nagpur-specific level, consistent with `VISION.md` Section 11.

| Metric | Threshold |
|---|---|
| Schema, locality ID standard, source registry format, and validation suite generalize to a second city without redesign | Demonstrated at v2.0 expansion (Nashik, Aurangabad, or Amravati) |
| Methodology document requires only data substitution, not structural rewrite, to onboard a new city | True |

---

## 13. Startup Readiness

Startup readiness is assessed only in the context of Version 4, where `VISION.md` Section 8 and Section 11 introduce civic SaaS API access, government collaboration, and data licensing as long-term possibilities — not commitments. This section evaluates whether the Product Success criteria in Section 8 are sufficient for institutional evaluation; it does not introduce a second, separate definition of product readiness.

| Metric | Threshold |
|---|---|
| A civic body or enterprise can evaluate the platform's data quality without engaging the team directly | True, via public validation reports and methodology documentation |
| A documented data licensing or API access model exists | Present only once pursued at v4.0; not a prerequisite for earlier versions |
| Revenue, funding, or commercial adoption | Explicitly not a success metric prior to v4.0, and not treated as a proxy for engineering quality at any version |

---

## 14. Research Impact

| Metric | Threshold |
|---|---|
| Dataset used in at least one independent academic, policy, or civic analysis outside the core team | Tracked as an outcome, not required for any version's release criteria |
| Methodology cited or adapted by an external party | Tracked as an outcome, not required for any version's release criteria |

Research impact is intentionally separated from Research Success (Section 5). Research Success measures whether the platform is *citable and reproducible*, which NagpurLens fully controls. Research Impact measures whether it *is in fact cited or reproduced*, which depends on external adoption and is therefore tracked but never used as a release gate.

---

## 15. Public Impact

| Metric | Threshold |
|---|---|
| A home buyer, investor, builder, or civic officer can answer one of the three core questions for a specific locality using only the public dashboard | Verified true at v1.0 for Question 1, and at each subsequent version for its corresponding question |
| Instances of the platform being cited as evidence in a real decision (civic, investment, or research) | Tracked as an outcome; not a release gate for any version |

---

## 16. Summary Table — Success by Version

| Dimension | v1.0 | v2.0 | v3.0 | v4.0 |
|---|---|---|---|---|
| Questions answered | 1 of 3 | 2 of 3 | 3 of 3 | 3 of 3, scaled |
| Core dataset | Localities + Infrastructure | + Growth signals | + Price/demographic data | Multi-city |
| KPIs live | IDI, PIR, HAS, MII | + GSI | + IAS | Same, city-agnostic |
| Product surface | Dashboard, API, website | Extended | Extended | Civic API, licensing model |
| Governance requirement | Full traceability to `VISION.md` | Same | Same | Same |

No dimension in this table is satisfied by feature count, popularity, or commercial traction alone. A version is successful only when its data is validated, its methodology is documented, and its outputs are reproducible by someone outside the core team.
