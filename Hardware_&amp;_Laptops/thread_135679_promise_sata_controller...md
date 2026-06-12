---
title: "promise sata controller.."
date: 2006-02-24
forum: Hardware &amp; Laptops
---

### Post by ShadyPete on 2006-02-24
I've been through all the guides I've found on this issue.  I updated to kernel version 2.6.15 which one of the guides I read suggested.. but the drive is not working still.

when i look at drives under the sys admin section i see /dev/fd0 i try to mount that volume but i get.. 

mount: special device /dev/fd0 does not exist

under fdisk all i see is.. 

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2389    19189611   83  Linux
/dev/hda2            2390        2495      851445    5  Extended
/dev/hda5            2390        2495      851413+  82  Linux swap / Solaris

i very newb at this so any help would be great thanks guys 

the card im using is promise sata300 tx2 plus
..

i just looked in my device manager and saw unknown scsi host adapter.. i'm thinking that is the issue just need to install driver prolly?

---

### Post by GTvulse on 2006-02-24
Check here to see if that driver really works for you: [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by nickle on 2006-02-24
I am fairly sure Dapper supports this controller; it certainly supports the Promise SATA300 TX4....

---

