---
title: "Setting up xp pro to run on a slave hd"
date: 2008-09-22
forum: General Help
---

### Post by dagoth_pie on 2008-09-22
I've got my Ubuntu 8.04 install on the master hard drive with a xp pro install on the slave, but I'm not sure how to go about setting up grub to detect the xp install and boot to it, I remember reading that windows can only boot from the primary partition, but that was by a windows basher, Is it possible to boot it from a second hard drive? or will I need to install a grub partition on the xp hard drive and set it as the master? any help will be appreciated, thanks in advance

---

### Post by prshah on 2008-09-22
> **dagoth_pie said:**
> I've got my Ubuntu 8.04 install on the master hard drive with a xp pro install on the slave, but I'm not sure how to go about setting up grub to detect the xp install and boot to it, I remember reading that windows can only boot from the primary partition, but that was by a windows basher, Is it possible to boot it from a second hard drive? or will I need to install a grub partition on the xp hard drive and set it as the master? any help will be appreciated, thanks in advance

Normally, windows can only boot from a primary partition, since only primary partitions can be set as "Active". But you seem a bit confused by the concept of a primary partition; you can have a primary partition on a secondary hard disk as well.

In any case, this point is moot when booting using GRUB. GRUB can successfully chainload the Windows partition, no matter what drive it is on or what type of partition (primary / logical "drive")

As to how to use GRUB, you can go through [this excellent tutorial]("http://www.dedoimedo.com/computers/grub.html").

---

