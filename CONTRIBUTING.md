# How to contribute to the Process Analytics project

[//]: # (These are general guidelines that applies to all repositories.)

[//]: # (Specific tasks may be required by the repository. It this case, create a dedicated `CONTRIBUTING.md` file in the repository.)

## Branching

### Branch Naming

Branch naming is essential for understanding the purpose of the branch and eventually, for automatically adding labels to the PR.

### Branch Naming Convention

```
<type>/<ISSUE_ID>_<short_description>
```

**Note**: `ISSUE_ID` is optional, but it is recommended to link the branch to an existing issue to ensure.

#### Types

Types are based on [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/#summary):
- `feat`
- `fix`
- `chore`
- `docs`
- `test`
- `ci`
- `refactor`
- `style`
- `perf`
- `build`
- `revert`

Additional types:
- `poc`
- `defect`

#### Example

If `194` is the GitHub issue ID and `feat` is the type:
```
feat/194_support_data_objects
```


## PR Conventions

### PR Size

Make PRs small to facilitate the review process.

- There are no strict metrics, but aim for one PR per feature or bug fix.
- Consider splitting a feature to iterate better and speed up review and integration.

### PR Title

We use the PR title as the commit message upon merging. Therefore, the PR title must conform to https://www.conventionalcommits.org/en/v1.0.0/[conventional commit].

In most repositories, if the PR title does not conform, the GitHub Actions workflow to check the PR title will fail and post a comment in the Pull Request. The PR creator must update the PR title.

This ensures consistent commits and allows the use of tools to generate changelogs and adhere to https://semver.org/[semantic versioning].

### PR Description

**IMPORTANT**: always follow the Pull Request template when creating a PR. Otherwise, we may not be able to review your PR which will then be rejected.

Facilitate the review by:
- Providing minimal context (used for the PR merge commit).
- Linking to the GitHub issue, if available.
- Including screenshots for all visual changes (before and after).

Provide screenshots for all visual changes:
- This helps greatly in understanding the context and facilitates review.
- Providing screenshots for before and after the changes also make things more concrete. They can then be used to fill the Release Notes.

### PR labels

**NOTE**: for maintainers only, external contributors without write access to the repository cannot add labels to PRs.

Labels are used to auto-generate a release notes. So, do not forget to add the relevant labels to the PR.


## Commit Message

### Commit Message Format

We always use `squash and merge`, so commit history cleanliness within the PR is not crucial.

### Skip CI in a Commit Message

⚠️ CI runs are expensive.

Use `[skip ci]` or `[no ci]` in commit messages to skip unnecessary CI runs.

ℹ️ For more details, see [Skipping workflow runs](https://docs.github.com/en/actions/managing-workflow-runs/skipping-workflow-runs).


## PR Management

### Pull Request in Progress

Learn how to mark the PR as `Draft` using [Converting a pull request to a draft](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/changing-the-stage-of-a-pull-request#converting-a-pull-request-to-a-draft).

This communicates that the PR is a _work in progress_ and avoids premature reviews.

### Force Push Policy

#### On Draft PRs

*Allowed.*

⚠️ When force pushing, use `force-with-lease` to avoid overwriting commits pushed by others. See [git-push](https://git-scm.com/docs/git-push).

#### On Active PRs

*Not allowed, unless agreed upon by reviewers.*

Force pushing on active PRs makes reviews hard to follow and prevents differences from previous commits after feedback has been integrated.

### PR Depending on Another PR

When it's possible, limit creating multiple dependent PRs, because:

- It increases PR backlog.
- It puts pressure on reviewers.
- It requires rebasing when the parent PR is merged.

Always apply the `depends on another PR` label and mark the PR as `Draft` to make dependencies explicit.


## PR Review

### Stay Aware for Review Needed

Set up GitHub notifications to stay updated on PR changes and review requests.

ℹ️ For more details, see [Configuring notifications](https://docs.github.com/en/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications).

### Choose Reviewers

**NOTE**: for maintainers only, external contributors without write access to the repository cannot add reviewers PRs.

Number of reviewers:
- **MUST** have at least 1 reviewer who is knowledgeable about the topic. This is generally enforced by a [ruleset](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)
- **_OPTIONAL_**: on a chosen topic, have 2 or more reviewers.

### Comment Convention

For effective reviews, adhere to "conventional comments" https://conventionalcomments.org/[guidelines].

Browser extensions to help apply these guidelines:
- ✔️ [Conventional Comments Web Extension](https://github.com/davidfou/conventionalcomments-web-extension). For Gitlab and GitHub, extension for Chrome and Firefox.

### Batch Suggestions

Merge suggestions in a batch to limit the number of commits and workflow executions.

ℹ️ See the documentation about [adding a suggestion to batch](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/incorporating-feedback-in-your-pull-request).

### Handle Discussions Efficiently

- Avoid long discussions in PR comments. Opt for direct conversations if needed.
- Seek help from others if no agreement is reached.


## Sources of inspiration

- https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/getting-started/best-practices-for-pull-requests
- https://opensource.guide/how-to-contribute/#opening-a-pull-request
- https://github.com/grafana/grafana/blob/main/contribute/create-pull-request.md
- https://github.com/prometheus/prometheus/blob/main/CONTRIBUTING.md#pull-request-checklist
