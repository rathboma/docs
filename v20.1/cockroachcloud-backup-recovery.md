---
title: Restore Data from a Backup
summary: Restore a table, database, or cluster from a backup.
toc: true
build_for: [cockroachcloud]
---

This page describes recovery workflows.

Cockroach Labs runs full backups daily and incremental backups hourly for every CockroachCloud cluster. The full backups are retained for 30 days and incremental backups for 7 days.

{{site.data.alerts.callout_info}}
All databases are not backed up at the same time. Each database is backed up every hour based on the time of creation. For larger databases, you might see an hourly CPU spike while the database is being backed up.
{{site.data.alerts.end}}

## Backup Recovery page

A list of your full cluster backups displays on your cluster's **Backup Recovery** page.

For each backup, the following details display:

- The date and time the backup was taken (**Data From**)
- The **Status** of the backup
- The **Type** of backup
- The **Size** of the backup
- The remaining number of days the backup will be retained (**Expires In**)
- The storage **Location** of the backup
- The number of [**Databases**](#databases) included in the backup
- Additional **Recovery Info**.

To view additional details or [to restore a cluster](#restore-a-cluster), click **View** in the **Recovery Info** column.

### Databases

To view the databases included in the backup, click the number in the **Databases** column on the **Backup Recovery** page.

For each database in the backup, the following details display:

- The **Name** of the database
- The **Size** of the database
- The number of [**Tables**](#tables) in the database
- Additional **Recovery Info**

To view additional details or [to restore a database](#restore-a-database), click **View** in the **Recovery Info** column.

### Tables

To view the tables included in a backup, click the number in the **Tables** column on the [**Databases**](#databases) page.

For each table in the backup, the following details display:

- The **Name** of the table
- The **Size** of the table
- The number of **Rows** in the table
- Additional **Recovery Info**

To view additional details or [to restore a table](#restore-a-table), click **View** in the **Recovery Info** column.

## Restore a cluster

To restore a cluster, navigate to your cluster's **Backup Recovery** page:

1. Click **View** for the cluster backup you want to restore.

    The **Recovery information** module displays.

1. Verify that you have enough space to restore the backup file.

    For daily backups, you need at least the space listed in the **Size** field above. For hourly backups, you need the **Size** plus the **Daily backup size**.

1. Verify that the target cluster does not have any user-created databases or tables. If you do not have a fresh cluster, `CREATE` a new one.

1. Copy the populated `RESTORE` statement.

1. In your command line interface, run the `RESTORE` statement.


## Restore a database

## Restore a table

## Backup and restore from a self-hosted CockroachDB cluster

You can [backup](backup.html) your self-hosted CockroachDB databases to an [external location](backup.html#backup-file-urls) and then [restore](restore.html) to your CockroachCloud cluster.

{{site.data.alerts.callout_danger}}
If you are backing up the data to AWS or GCP, use the `specified` option for the `AUTH` parameter.
{{site.data.alerts.end}}

## Back up and restore data on your own

Additionally, you can [back up and restore](backup-and-restore.html) data on your own.
