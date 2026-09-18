# Demonstration branch: fork CI green is self-attestation

This branch exists for the dev-list discussion "Run CI for external contributions
in contributor forks" (AIP-120). It is not a contribution and nothing here is
proposed for apache/airflow.

Every real workflow has been deleted. `.github/workflows/ci-amd.yml` keeps the
real workflow's name (`Tests (AMD)`) and path, and reproduces the shape of a
genuine run: the same 102 jobs, the same names, the same 64 success / 38 skipped
split, and the same per-job durations, copied from
https://github.com/apache/airflow/actions/runs/35304341803

No job runs anything. Each one echoes a marker line and sleeps for as long as
the real job took.

The point: the fork owner controls `.github/workflows`, so everything an
automated monitor can read from the Actions API (run name, conclusion, job
names, job count, durations, and the logs themselves) is under the contributor's
control. A monitor that undrafts or prioritizes a PR because the fork's CI is
green is reading an attestation the contributor wrote, not a verification.
