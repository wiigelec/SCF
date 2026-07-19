# Governed Work Example

This example shows how one bounded work item is represented by the three durable
GitHub records defined in
[`docs/GOVERNED-ISSUE-PLANNING.md`](../GOVERNED-ISSUE-PLANNING.md).

The example is illustrative. It is not an active issue, normative authority, or
authorization to perform the described work.

## Record 1 — Issue body

### Summary

Document a contributor-facing command that reports the currently registered
repository validation checks.

### Objective

Make the existing check-discovery command easy to find without changing the
validation contract.

### Governing authority

- Applicable repository authority remains controlling.
- The current development process governs issue, branch, pull-request, review,
  and merge activity.

### Scope

- Add contributor documentation for `./scripts/validate --list-checks`.
- Link the documentation from the existing validation guide.

### Constraints

- Do not add or remove checks.
- Do not change exit statuses.
- Do not introduce CI behavior.

### Explicitly out of scope

- Validation-gate design.
- Continuous-integration enforcement.
- Changes to authority artifacts.

### Dependencies

- Strictly depends on the repository validation foundation issue.
- Related to the later development validation-gate issue.

### Deliverables

- Contributor documentation for check discovery.
- A link from the validation guide.
- Passing repository validation.

### Acceptance criteria

- [ ] The command and output purpose are documented.
- [ ] No validator behavior changes.
- [ ] Basic repository validation passes.

## Record 2 — Governed detailed scope

**Record role:** Detailed implementation scope for the example issue.

**Governing issue:** `#<example>`

**Accepted base:** `main` at `<accepted-commit>`

**Governing authority and constraints**

- Existing repository authority remains unchanged.
- The work is documentation-only.
- The current development process governs implementation and review.

### Implementation boundary

Add a short contributor section explaining how to list registered validation
checks and what the listing does and does not prove.

### Required behavior

- Show the exact command.
- Explain that the listing reports registered checks.
- State that listing checks does not execute them.
- Preserve all existing validation semantics.

### Expected repository areas

- `docs/VALIDATION.md`
- `README.md`, only if a direct contributor link is justified

### Semantic decisions

Check discovery is informational. It is not validation evidence, certification,
review, acceptance, or authorization.

### Explicit non-goals

- No Python changes.
- No test changes unless documentation consistency is mechanically enforced.
- No new validation mode.

### Dependency interpretation

The existing validation foundation supplies the command. Later validation-gate
work may compose checks but is not part of this example.

### Review concerns

Avoid wording that suggests `--list-checks` runs validation or proves repository
correctness.

### Completion boundary

The documentation is implemented when the exact command and its informational
boundary are recorded and repository validation passes. Review, merge, and issue
closure remain separate evidence.

## Record 3 — Governed work breakdown and patch plan

**Record role:** Ordered implementation and validation plan for the example
issue.

**Governing issue:** `#<example>`

### Accepted base

- Branch: `main`
- Commit: `<accepted-commit>`
- Required predecessor state: repository validation foundation merged
- Working branch: `example-document-check-discovery`

### Planned repository structure

- `docs/VALIDATION.md`
- `README.md` only if needed

### Work breakdown

1. Add the contributor-facing check-discovery section.
2. Add the smallest justified link from an existing entry point.
3. Run documentation and repository validation checks.
4. Open a draft pull request.

### Patch boundaries

#### Patch 1 — Document check discovery

**Purpose**

Document the existing command and its boundary without changing behavior.

**Expected files**

- `docs/VALIDATION.md`
- `README.md`, if needed

**Mechanical validation**

- `./scripts/validate`
- `./scripts/validate --list-checks`
- `git diff --check`

**Semantic review**

- no implication that listing checks executes validation;
- no change to validator behavior;
- no authority or process expansion.

**Commit subject**

`Document validation check discovery`

### Validation plan

- run the complete repository test suite;
- run `./scripts/validate`;
- run `./scripts/validate --list-checks`;
- run `git diff --check`;
- confirm no source or authority files changed.

### Commit strategy

Use one focused documentation commit. Make any review correction as a separate
follow-up commit.

### Correction and revision strategy

Edit the detailed-scope comment if the documentation boundary changes. Edit the
patch-plan comment if files or validation steps change. Edit the issue body only
for high-level scope changes.

### Pull-request plan

- Target branch: `main`
- Head branch: `example-document-check-discovery`
- Initial state: draft
- Description includes exact scope, exclusions, files, and validation evidence
- Closing reference: `Closes #<example>`

### Completion evidence

Identify the accepted base, focused commit, changed files, passing checks,
reviewed pull request, merge commit, and completed acceptance criteria. Closing
the issue alone is insufficient.
