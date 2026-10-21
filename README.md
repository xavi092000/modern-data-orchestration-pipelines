# Data Orchestration Exercises with Kestra

Learning workflows covering Python tasks, PostgreSQL taxi ingestion, and scheduled AWS S3 / Redshift ingestion.

## Origin and contribution scope

The workflows use the `zoomcamp` namespace and reference DataTalksClub course data. They are **course-based exercises and adaptations**, not a claim of an original enterprise orchestration platform. See [Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp).

The public work includes AWS/Redshift workflow configuration, monthly schedules, staging tables, and SQL merge logic. The precise upstream-versus-personal line attribution has not been reconstructed; the published code is available for inspection.

## Files to review

| File | Purpose |
|---|---|
| [04_postgres_taxi.yml](04_postgres_taxi.yml) | PostgreSQL ingestion exercise |
| [08_aws_taxi.yml](08_aws_taxi.yml) | AWS ingestion workflow |
| [09_aws_taxi_scheduled.yml](09_aws_taxi_scheduled.yml) | Monthly S3 / Redshift workflow |

## Configuration and validation

Import the desired YAML into a compatible Kestra installation. Configure AWS access and the Redshift secret references used in the workflow in your own environment; review bucket names and resource settings before enabling schedules. These workflows use cloud services and can incur charges.

The scheduled green-taxi load issues one `COPY` and deduplicates identical source rows before `MERGE`. The yellow-taxi path uses a persistent staging table with explicit truncation so separate SQL tasks do not depend on a session-local temporary table. These corrections have not been executed against a live Redshift cluster during the portfolio review.

No production deployment, current cloud availability, or end-to-end runtime success is claimed by the presence of these YAML files. A real replay should confirm stable target row counts and unique business keys before operational use.

Maintained by Felix Brillant.
