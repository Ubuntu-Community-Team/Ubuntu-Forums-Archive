---
title: "Reorder of drive nodes in /dev"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by Yakov Hrebtov on 2007-11-19
I want my system drive to be always in the same place - /dev/sda.

My system drive connected to the SATA0 on the motherboerd. There is also PCI-E 3ware SATA RAID controller installed.
Ubuntu shows system drive node always after nodes of arrays defined on the RAID controller. Changing configuration of the RAID arrays (adding/deleting arrays) causes my system drive to walk from /dev/sdb to /dev/sdc, /dev/sdd and back.
This is not very good for me. Though partitions of system drive are always mounted well using UUIDs, I want to nail the first drive node (/dev/sda) to the system drive -- the main and permanent drive of the system.

How can i do such setup. Can I do it using udev? How?

Thanks in advance.

---

