---
title: "GRUB and RAID issue. (Error 2/GRUB)"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by mihxtc on 2009-07-13
Greetings, I'm a linux newbie and after installation GRUB gives error 2. I'm using RAID and I've tried with RAID 0 and 1 but both still give the same error.I searched these forums but every thread seems to have different solutions, none which seems to make sense to me. By reading those threads, I've concluded that fdisk -l output helps so here it is

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05000000

Disk /dev/sdb doesn't contain a valid partition table
I don't know how to interpret this information though. I have no idea where to begin to troubleshoot this. Any help would be very much appreciated. Thank you.

---

### Post by realzippy on 2009-07-13
Hi,
what do you mean: " I am using RAID? "

You are using a hardware RAID controller?
Or an Fakeraid?

Or are you attempting to set up a software RAID?

greetz from hamburg

---

### Post by mihxtc on 2009-07-13
yes, a RAID controller (Hardware). It was setup as RAID 0 before the installation.

---

### Post by realzippy on 2009-07-13
O.K.
So,what Raid controller are you using?

---

### Post by mihxtc on 2009-07-13
hold one second please, i'm searching for it. Thanks for help

---

### Post by mihxtc on 2009-07-13
integrated Nvidia Nforce 4 Intel Edition SATA RAID Controller

---

### Post by realzippy on 2009-07-13
This is no real hardware Raid controller.
It is a so called "Fakeraid".
fdisk shows that there are 2 harddisks,each with 80 GB (sda and sdb).
No way to use the mainboard-fakeraid-controller.
You should setup a Software RAID0,which works pretty fast under linux..

---

### Post by mihxtc on 2009-07-13
Ok thank you, what RAID software is available for Ubuntu?

---

### Post by mihxtc on 2009-07-13
Nevermind, I think I have found my solution here.

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)


Thank you for pointing me in the right direction. Thanks!

---

### Post by realzippy on 2009-07-13
mdadmin.
First thing you have to do is to disable the Raid option in your mainboard
bios.Also you should use the Alternate install CD.When it comes to partition
options you have to choose "manual".There you have to setup your RAID0 before going on with installation.I used to write a HowTo for Fedora,
which should help you:

[http://forums.fedoraforum.org/showthread.php?p=1112731](http://forums.fedoraforum.org/showthread.php?p=1112731)

If there will be problems,feel free to ask...

---

### Post by mihxtc on 2009-07-13
What is an alternate install CD? Actually I'm trying to install Mint. I tried Ubuntu first but got the same error so I didn't think it mattered if I was using Mint or Ubuntu. 


I don't think there is alternate CD for Mint :(

---

### Post by realzippy on 2009-07-13
[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

It is a text based install CD,no live CD.
Do not know if there is one for mint.
Mint is Ubuntu for the lazy.. ;-)

---

### Post by mihxtc on 2009-07-13
Okay, I'm all set. Thank you for your help. Cya!

---

