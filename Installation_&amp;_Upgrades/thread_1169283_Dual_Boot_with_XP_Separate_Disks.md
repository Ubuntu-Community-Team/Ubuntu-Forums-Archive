---
title: "Dual Boot with XP Separate Disks"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by Westie2008 on 2009-05-25
I've browsed quite a number of topics about dual booting but haven't found the exact answer I'm looking for.

I've got an old Dell 8300  maxed out with two SATA HDDs and two older PATA HDDs.  I want to install Ubuntu 9.04 on the entire fourth HDD.  I tried using the LiveCD installer and despite it not finding any operating systems on this computer(!) I went ahead and let it install using the entire disk sdb.  I'm assuming that Linux is there but the pc boots straight to XP. No bootloader or whatever...

Using Gparted I see that sdc1 is Dell Utility partition, sdc2 is main Windows XP partition.  I want to install on sdb and it is formatted as sdb1 ext3, sdb2 extended, sdb5 linux-swap (which appears to be inside sdb2 from what I can tell from Gparted?)- I assume this is a result of what the installer did.

I also have an sda1 used for data, and sdd1 and sdd2 for more data.  I don't want to touch any of these.

From the reading I've done I think that I have to install Grub somewhere and get the computer to boot sdb1 first.  Can anyone explain how I can do this?  Physically, this drive I want to use is slaved on the second PATA slot... TIA!

---

