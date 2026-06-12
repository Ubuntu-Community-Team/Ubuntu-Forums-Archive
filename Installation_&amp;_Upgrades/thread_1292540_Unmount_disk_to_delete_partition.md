---
title: "Unmount disk to delete partition"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by srliem on 2009-10-16
I made some kind of mistake installing 9.04 UNR onto a Dell inspiron 1011 which had the Dell version Ubuntu 8.04 on it.

Currently there are two partitions, one with 9.04 on it and one with 8.04 on it. If I boot up with 8.04 it's fine, but I can't boot up with 9.04.

I want to delete 9.04 partition and reinstall it. 

For some reason the Dell version of 8.04 does not have a partition editor and I don't know how to do it from there.

When I boot UNR from a USB drive and try to delete the partition using Partition Editor, it says "Unable to delete /dev/sda5 Please unmount any logical partitions having a number higher than 5"

When I try to select Partition > Unmount, it is not offered as an option. There are also little key icons by the partition I'm trying to delete.

How do I unmount that partition so i can delete it and create a new one to reinstall on?

Thanks.

---

### Post by hal10000 on 2009-10-16
on your 8.04 system you can install gparted: 
[COLOR="Red"]sudo apt-get install gparted[/COLOR]

To unmount your sda5 close all file-manager windows and any apps that are currently access any data on sda5 and try in a terminal window

[COLOR="Red"]sudo umount /dev/sda5[/COLOR] (you see, the command name is **umount**, not unmount)

---

### Post by ztomic on 2009-10-16
> When I boot UNR from a USB drive and try to delete the partition using Partition Editor, it says "Unable to delete /dev/sda5 Please unmount any logical partitions having a number higher than 5"


You may need to use Swapoff. The UNR boot is probaly using the swap partition.

---

### Post by srliem on 2009-10-17
> **hal10000 said:**
> on your 8.04 system you can install gparted: 
[COLOR=Red]sudo apt-get install gparted[/COLOR]


Thank you. This allowed me to partition the drive from the 8.04 system. That problem has been solved

---

