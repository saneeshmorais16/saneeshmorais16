# GitHub portfolio audit and publication report

Completed work: 20–21 October 2026. Account: [saneeshmorais16](https://github.com/saneeshmorais16).

## Profile and organisation

- Updated the bio to the exact graduate wording requested.
- Replaced the broken profile website URL with [the working portfolio](https://saneeshmorais16.github.io/Saneesh_Portfolio_16/).
- Rewrote the profile README with six featured repositories, core skills, contacts, and accurate project links.
- Corrected the legacy portfolio README URL and student title, preserving its content and history.
- Updated descriptions and topics for all six featured repositories.
- Identified [smart-mixologist-fullstack](https://github.com/saneeshmorais16/smart-mixologist-fullstack) as the implementation. Added reference READMEs to the two licence-only variants and labelled the empty variant in repository metadata.
- No repositories were deleted or renamed and no force pushes were used. Event-Triage remains private.

## Published repository changes

| Repository | Commit | Local tests | CI run |
| --- | --- | ---: | --- |
| [mlflow-end-to-end-ml-pipeline](https://github.com/saneeshmorais16/mlflow-end-to-end-ml-pipeline) | [bf2addc](https://github.com/saneeshmorais16/mlflow-end-to-end-ml-pipeline/commit/bf2addcec34b55b89b9cffce7c759017fb891746) | 4 passed | [success](https://github.com/saneeshmorais16/mlflow-end-to-end-ml-pipeline/actions/runs/39556322566) |
| [rag-pipeline-from-scratch](https://github.com/saneeshmorais16/rag-pipeline-from-scratch) | [67ef2ec](https://github.com/saneeshmorais16/rag-pipeline-from-scratch/commit/67ef2ecfa21483fb74c152ee493b026456f44d7a) | 8 passed | [success](https://github.com/saneeshmorais16/rag-pipeline-from-scratch/actions/runs/39557076268) |
| [ai-code-review-tool](https://github.com/saneeshmorais16/ai-code-review-tool) | [4fac5ec](https://github.com/saneeshmorais16/ai-code-review-tool/commit/4fac5ec11c8c51b07e2e99fa59ef882534ef29ff) | 13 passed | [success](https://github.com/saneeshmorais16/ai-code-review-tool/actions/runs/39556332143) |
| [RAI-AuditUK-v1](https://github.com/saneeshmorais16/RAI-AuditUK-v1) | [91f5c90](https://github.com/saneeshmorais16/RAI-AuditUK-v1/commit/91f5c900af1527be5580ac6b6d5be0e3928dd529) | 3 passed | [success](https://github.com/saneeshmorais16/RAI-AuditUK-v1/actions/runs/39557080606) |
| [promptops-studio](https://github.com/saneeshmorais16/promptops-studio) | [33c1b83](https://github.com/saneeshmorais16/promptops-studio/commit/33c1b832364413fe501703742aaa23077f37142b) | 8 passed | [success](https://github.com/saneeshmorais16/promptops-studio/actions/runs/39556340715) |
| [ai-agent-observability-dashboard](https://github.com/saneeshmorais16/ai-agent-observability-dashboard) | [b1ff1cf](https://github.com/saneeshmorais16/ai-agent-observability-dashboard/commit/b1ff1cfc6da9d901a082db59c6c03724fcedb7da) | 10 passed | [success](https://github.com/saneeshmorais16/ai-agent-observability-dashboard/actions/runs/39556344556) |

## Fixes and evidence

- **MLflow:** separate train/validation/test sets prevent model selection on the test set; validation F1 selects the winner. Added a majority-class baseline, saved test metrics, a real inference request/response, and a regression assertion for selection methodology.
- **RAG:** closed SQLite connections explicitly, fixed extractive citations to include only quoted sources, exposed deterministic hashing mode, and made fallback warnings visible. Added connection and citation regression tests, a labelled fictional corpus, both embedding-mode results, and an actual local UI screenshot.
- **Code review:** Python AST detection avoids treating comments and strings as executable calls. Added six regression cases, 22 labelled synthetic evaluation snippets, per-case outcomes, and an actual local UI screenshot.
- **CI compatibility:** RAG and RAI initially failed Linux collection when invoked through the `pytest` executable. Explicit root-path configuration now makes both pytest command forms import the application consistently.
- **RAI-AuditUK, PromptOps, observability:** ran their existing suites, linked verification records, and polished metadata. PromptOps illustrative scores are now explicitly labelled as illustrative rather than measured.

## Measured results

All datasets are synthetic/fictional. These small development evaluations are not production benchmarks.

| Project | Dataset and result |
| --- | --- |
| MLflow | 600 generated rows; 360 train / 120 validation / 120 test. Random forest test accuracy 70.83% vs majority baseline 67.50%; F1 0.5070; ROC-AUC 0.7404. |
| RAG semantic | 12 documents, 24 answerable and 6 unanswerable questions. Top-1 retrieval 100%; citation document precision 85.71%; unanswerable rejection 33.33%. |
| RAG hashing | Same corpus. Top-1 retrieval 87.50%; citation document precision 75%; unanswerable rejection 0%. |
| Code review | 22 labelled snippets: TP 9, FN 2, FP 1, TN 10. Detection 81.82%; false-positive rate 9.09%; precision 90%. |

Each flagship repository contains `evaluation/` runners and raw JSON, plus `docs/EVALUATION.md` and `docs/DEMO.md`. Failed examples remain in the recorded results.

## Verification boundaries

46 local tests passed across the six repositories. Python source compilation passed for their application/evaluation modules. Fresh-checkout benchmark JSON matched the saved output exactly for MLflow, hashing RAG, and code review. Fresh Git clones of all three flagship commits passed tests, dependency consistency checks (`pip check`), and evaluation runners without copied runtime artefacts. These clone checks reused the isolated installed Python environments; they were not new dependency installations. GitHub Actions performs the independent Linux checkout/install/test runs linked above.

Unauthenticated HTTP checks returned 200 for the profile, canonical portfolio, six repository pages, verification records, all three flagship demo/evaluation guides, and both screenshot assets. Changed Markdown relative links were checked. Added/changed text was screened for high-confidence credential patterns; this is not a full historical secret audit. The code-review and RAG screenshots show actual local runs; MLflow's demo contains an executed API exchange.

## Remaining blockers and limitations

- Profile pins remain unchanged. GitHub's public GraphQL mutation schema has no profile-pin operation, and the available browser session is signed out. The six projects are featured in the README; changing pins requires a signed-in browser.
- Docker is unavailable locally, so the existing MLflow Docker image was not built or run. No public hosted application demo was created; the committed demos are reproducible locally.
- RAG similarity gating still answers four of six unanswerable semantic-mode questions. Citation document relevance does not prove answer correctness.
- The code scanner still misses aliased/dynamic execution and flags a secret-shaped comment. Its diagnostic set is deliberately retained, not filtered to inflate performance.
- RAI's original CSV/PDF artefacts were preserved; their external data provenance and licensing were not established by this audit. Only the synthetic audit tests were run.
- Old dependency deprecation warnings remain. Passing tests do not certify security or production readiness.
