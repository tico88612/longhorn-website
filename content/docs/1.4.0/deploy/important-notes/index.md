---
title: Important Notes
weight: 4
---

This page lists important notes for Longhorn v{{< current-version >}}.
Please see [here](https://github.com/longhorn/longhorn/releases/tag/v{{< current-version >}}) for the full release note.

## Notes
### Supported Kubernetes Versions
Please ensure your Kubernetes cluster is at least v1.18 and at most v1.24 before upgrading to Longhorn v{{< current-version >}} because the supported Kubernetes version has been updated (>= v1.18 and <= v1.24) in v{{< current-version >}}.
### Recurring Jobs
After the upgrade, the recurring job settings of volumes will be migrated to new recurring job resources, and the `RecurringJobs` field in the volume spec will be deprecated. [[doc](https://longhorn.io/docs/{{< current-version >}}/deploy/upgrade/#4-automatically-migrate-recurring-jobs)]
### Backup Migration Time
When upgrading from a Longhorn version >= 1.2.0 and <= v1.2.3 to v{{< current-version >}}, if your cluster has many backups, you may expect to have a long upgrade time (with 22000 backups, it could take a few hours). Helm upgrade may timeout and you may need to re-run the upgrade command or set a longer timeout. This is [a known issue](https://github.com/longhorn/longhorn/issues/3890).
### Longhorn uninstallation
To prevent Longhorn from being accidentally uninstalled (which leads to data lost),
we introduce a new setting, [deleting-confirmation-flag](../../references/settings/#deleting-confirmation-flag).
If this flag is **false**, the Longhorn uninstallation job will fail.
Set this flag to **true** to allow Longhorn uninstallation.
See more in the [uninstall](../uninstall) section.