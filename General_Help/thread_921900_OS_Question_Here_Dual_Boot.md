---
title: "OS Question Here Dual Boot"
date: 2008-09-16
forum: General Help
---

### Post by thomas.mckay on 2008-09-16
I has windows xp installed on a hard drive in my computer. I then installed Ubuntu on a separate hard drive, so i have Windows on one and Ubuntu on the other. If they're both plugged in, shouldn't I see a menu that gives me the option to chose which OS I want to boot into? If I set Windows HD as primary bot device it boots into windows, and if I set the Ubuntu HD as primary boot device it boots into Ubuntu, and when I hit ESC to get into the boot menu, I only see the 3 Ubuntu options to boot into. how can I change this so i can also boot into Windows if I want to?

And I have VMWare that I plan to set up. How do I go about doing that, or is it straight forward?

---

### Post by rraj.be on 2008-09-16
Plug in both hard disks.

Boot into ubuntu.

open terminal and type

```
sudo grub

find /boot/grub/stage1

```
if it returns like
```

[hdX,Y]
```

Then type```
 root [hdX,Y]

setup [hdX,Y]
```

This will search for all OS available and reinstall the grub.

---

### Post by thomas.mckay on 2008-09-16
I can follow those up until where [hdX, Y] is supposed to come up. (hd0, 0) shows up and anything I type after that it says Error 11: unrecognized device string

---

### Post by jerome1232 on 2008-09-16
I don't think there's supposed to be a space after the comma, it would be hd0,0

---

### Post by thomas.mckay on 2008-09-16
Still just boots straight into Ubuntu

---

### Post by rraj.be on 2008-09-16
> **thomas.mckay said:**
> Still just boots straight into Ubuntu

Post the output of sudo fdisk -l

Had you connected both hard disks while reinstalling GRUB

---

### Post by thomas.mckay on 2008-09-16
Yes both were connected

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
tom@Tomcomp1:~$ 

What do I do?

---

### Post by caljohnsmith on 2008-09-16
When you are in Ubuntu, open up your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
At the bottom, add the following:
```
title	   Windows
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
Reboot, and let me know if you get any errors when choosing the Windows entry from the Grub menu.

---

### Post by rraj.be on 2008-09-16
> **thomas.mckay said:**
> Yes both were connected

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
tom@Tomcomp1:~$ 

What do I do?

Put this exactly in terminal and post the op

```
sudo fdisk -l
```

---

### Post by thomas.mckay on 2008-09-17
It asks for my password then says unable to reply

---

### Post by Sef on 2008-09-17
> It asks for my password then says unable to reply
```
sudo fdisk -l
``` Small L -   Did you type a small L?

---

