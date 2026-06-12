---
title: "Installed 8.10 on USB key: missing files (how to do an installation check?)"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-01-29
I have just installed Ubuntu 8.10 on my 8Gb USB key. I had used the install CD and pointed the installation to the USB key. I had also told it to install the GRUB on it. Prior to the installation, I had used Partition Editor to create a 2Gb Swap on it and the rest as Ext3.

But when I boot with it, it said it is missing files. I do not remember exactly what but I think it said something about dev, proc folders and others.

The installation went without problems at all. Well the only problem I have is because of my hardware setup. I cannot boot with my USB on my home PC because it does not detect it and causes my USB keyboard + USB mouse to not work until I actually boot into an O/S.  To workaround this, I have created a USB Boot cd from pendrive linux site and tried to add its menu.lst into my main menu.lst but both ways, when booting with my USB Ubuntu O/S, it says there are missing files.

Is there a way from my HD Ubuntu, to do a system or installation check on it to tell me everthing that is wrong or missing, AND fix it ?

I want to use this USB key for the office (on VPNed PCs connected to the office, at the office, ...).

P.S. : I do not want to have a LIVE CD version on a USB key. I want a full functional Ubuntu 8.10 with logon-ids and persistent, also updatable.

[added stuffs]> 
> fdisk -l

Partition table entries are not in disk order

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         261     2096451   82  Linux swap / Solaris
/dev/sdc2   *         262         974     5727172+  83  Linux

---

### Post by Browser_ice on 2009-01-29
Somehow, I get the feeling this thread is going to slip to page 15 without getting an answer.

---

### Post by zwygart on 2009-01-29
Hi, 
First it is not recommended to have swap on flash memory because they have a limited number of times that you can write on it. So putting a Swap will use them prematuraly. 

About the errors you said I think that your menu.lst is correct. If not you will be unable to boot your system.

Here is what could be your problem : your fstab. You have installed your system correctly by using the CD. But when you installed your drive where sdc. But when you boot on the USB it becomes sda. So your fstab is setted to sdc which does not right when you boot the USB. 

The dev and proc are mounted at boot time to have infos about the system and processes.

How to fix this. On your USB go to /etc/fstab and replace all /dev/sdc with /dev/sda. 
Also you might try to add to your /boot/grub/menu.lst the option root=/dev/sda2 to the line of the kernel.

Good Luck, it is possible what you want to do. 
Post also more infos about the error and when it happens, your fstab and menu.lst.

---

