---
title: "External Hardrive Not Mounting"
date: 2009-05-03
forum: Hardware
---

### Post by iPower-X2 on 2009-05-03
Hi i have just joined and had Ubuntu 8.04 for a couple of months and i can not mount my external Maxtor basics 1TB

---

### Post by x22 on 2009-05-03
welcome to the forum

try "fdisk -l" to see whether the drive is recognized
by the system: partitions being "sda1" and "sda2" let's say.
then "mount /dev/sda1 /mnt" should mount the first partition

if the drive isn't recognized, then maybe you have a USB
problem.  Try "lsmod |grep usb_storage" to see whether the
appropriate module(s) are loaded.

then report back, please

---

### Post by iPower-X2 on 2009-05-03
nothing came up in terminal

---

### Post by iPower-X2 on 2009-05-03
oh it says "Mount: only root can do that"

---

### Post by SpiXe on 2009-05-03
> **iPower-X2 said:**
> oh it says "Mount: only root can do that"


Put "sudo" in front of the command :) Makes you root (If Im not very wrong..)

SpiXe

---

### Post by iPower-X2 on 2009-05-03
i did every thing both of you said i still cannot mount my hdd:confused:](*,)

---

### Post by mikedep333 on 2009-05-03
My suggested advise is to see if it is visible with the graphical utility, gparted. To install the package "gparted" from the terminal, run:
```
sudo apt-get install gparted
```

It should then be under system > administration > partition editor.

It should then look like this.
[IMG]http://gparted.sourceforge.net/screens/gparted_1_big.jpg[/IMG]
By default it should be on /dev/sda or whatever your internal hard drive is in the top right.

See if there are any other drives listed in that drop down list in the top right. Tell us what partitions, with what filesystems are on them.

Also, tell us, did you just take this hard drive from a windows computer? If so, the simple solution is likely to force a filesystem/drive check on it from windows, and then properly eject it. You can right click on the drive from my computer, and go to properties to check it.

---

### Post by iPower-X2 on 2009-05-03
yes it has a came from a windows server and vista but the partion manger does not see the external drive

---

### Post by iPower-X2 on 2009-05-03
ah it is fixed now:P:P:P:D:mrgreen:

---

### Post by mikedep333 on 2009-05-03
Glad to hear it. Did you run the disk check under Windows?

---

### Post by iPower-X2 on 2009-05-03
yes and no it taked to long

---

