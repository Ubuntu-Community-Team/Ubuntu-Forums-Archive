---
title: "Overprovisioning SSD"
date: 2018-05-27
forum: Hardware
---

### Post by hrsetrdr on 2018-05-27
Several days ago overprovisioning an SSD was mentioned, I can't find the thread, but I did have a question:    Would the "overprovisioning" benefit be satisfied by shrinking a partition with gparted in a live session?

Or, would Ubuntu have to be reinstalled, and reserving drive space for overprovisioning done during partition setup?      Is using a swap partition on an nvme ssd NOT a good idea?   Or, does it matter?

---

### Post by kerry_s on 2018-05-27
most makers build that right into the ssd. but you can check in disks how yours is setup. some os's do leave space. i know fedora does.

ubuntu uses a swap file in place of a partition. i'm using solus budgie & they still use partitions.

[ATTACH=CONFIG]279889[/ATTACH]

---

### Post by hrsetrdr on 2018-05-27
Mine has an EFI partition, an EXT4 and swap partition.   If OP is already in then I won't worry.

[ATTACH=CONFIG]279890[/ATTACH]

---

