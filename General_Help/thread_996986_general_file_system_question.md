---
title: "general file system question"
date: 2008-11-29
forum: General Help
---

### Post by StOoZ on 2008-11-29
what the last two partitions are meant for ??
[PHP]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris
[/PHP]

---

### Post by taurus on 2008-11-29
/dev/sda2 is just an extended partition and under that extended partition, you have your swap partition as a logical partition.

Meanwhile, /dev/sda1 is your first primary partition.

---

