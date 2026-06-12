---
title: "SSD Drive stopped working ???"
date: 2024-02-04
forum: Hardware
---

### Post by creature1963 on 2024-02-04
Been working fine last year.

but when to do monthly backup of the drive a few days back and the drive is not h there !

Rebooted and entered BIOs, drive is is found and picked up correctly.

Rebooted Ubuntu 22.04 

opened drives, finds harddrive, but will not let me mount, format, delete or create partition !

opened Gparted and ssd is NOT there ???

Any ideas please

---

### Post by TheFu on 2024-02-04
SSD storage fails sometimes, just like all HDDs.  Backups aren't optional. Perhaps monthly isn't often enough?  When SSDs fail, they usually just stop working and that's it. No warning at all.  

Have you looked in the system logs for warnings and errors about it?

Have you run SMART tests and SMART reports against the device?  What do they show?  **smartctl** is the tool for this. There are others with **nvme** drives.  I run weekly short tests for all my storage to help predict failure BEFORE it happens.  I do monthly long tests as well.

All storage fails. This is to be expected.  From time to to time, cables that connect the storage to the drive controller fail too, so check those out, if there are any.

---

