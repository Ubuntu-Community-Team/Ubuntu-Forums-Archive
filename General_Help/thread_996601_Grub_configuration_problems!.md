---
title: "Grub configuration problems!"
date: 2008-11-29
forum: General Help
---

### Post by manij on 2008-11-29
Hi,

I have three HD two SATA and a PATA

Here is the Sudo fdisk -l output
[I][B]
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec260083

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3769    30274461   83  Linux
/dev/sdb2            3770        4012     1951897+   5  Extended
/dev/sdb5            3770        4012     1951866   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84788478

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5024    40355248+  83  Linux
/dev/sdc2            5025        5288     2120580   82  Linux swap / Solaris
/dev/sdc4            5289       14593    74742412+   b  W95 FAT32[/B][/I]

But my grub menu looks at it slightly differently.

Its sees **sdc** as hd1. It boots onto the Hardy installation on this drive no problem. I'm posting from it!

Here is my challenge, I have ibex installed on what is listed as ** sdb** in fdisk -l, but the old grub loads from "**sdc**" and ignores the ibex installation.

I can instruct it to load another grub from "** sdb**", but that will interfere with the current menu.lst, becos it sees the hardy installation as ** sdb**.

How or why did my SUDO fdisk get screwed up this way?

It used to be sata 1 **sda** with no linux, sata 2 **sdb** with hardy and pata **sdc** as a FAT32.

HELP!

---

### Post by manij on 2008-11-29
There seems to be grub vs Fdisk -l conflict

how do I fix this?

---

### Post by gTinker on 2008-11-29
Modify the stanza for each distro in the menu.lst to use the UUID of its partition rather than device node for the root= portion of the kernel line.

Example:
#kernel		/boot/vmlinuz-2.6.18-6-686  root=/dev/hdg3 ro vga=789
kernel		/boot/vmlinuz-2.6.18-6-686  root=UUID=190011e9-df67-4b9b-b1a7-fab3a8afabf6 ro vga=789 


Note: 
UUIDs for your system partitions are available in the block id table, /etc/blkid.tab or by typing sudo blkid.

IF you have labels on the partitions GRUB can mount by LABEL= as well as UUID or device node.

---

### Post by caljohnsmith on 2008-11-29
Actually, your fdisk output is not messed up about how it orders the drives. :) Basically, the Grub you use on start up is not the same as the Grub that you use in Ubuntu when it comes to how the drives are ordered. 

When you use Grub in Ubuntu, Grub works through the kernel, so Grub's drives are ordered the same as Ubuntu orders them in the /dev directory; the drives are generally ordered as IDE, SATA, USB, etc:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc.
```
But on start up, Grub must use BIOS to access the drives, so **Grub on start up sees the order of drives as the same as the BIOS boot order** (and you can change the BIOS boot order); that means the drive order Grub sees on start up has nothing to do with how the drives are ordered in /dev when you are in Ubuntu. Therefore, on start up, Grub sees:
```
(hd0) = 1st boot drive (the drive you boot on start up)
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
So bottom line, when you run Grub commands in Ubuntu, the first case above applies, but when you boot Grub on start up, the second case applies; and since Grub uses the menu.lst on start up, the second case applies when it comes to determining the correct OS entries in the menu.lst. Since Grub sees sdc as (hd1) on start up, that just means sdc is second in the BIOS boot order. 

Can you set your BIOS to boot the Intrepid sdb drive? If so, you can install Grub to its MBR and make it bootable with:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
And then you should be able to boot the sdb drive and get the Intrepid boot menu. How about trying that first and let me know how far you get or if you run into problems.

---

### Post by manij on 2008-11-29
[B][I]
Can you set your BIOS to boot the Intrepid sdb drive? [/I][/B]

How do I do this? Just set the boot order in the bios? It is the first drive in the system!

---

### Post by gTinker on 2008-12-02
If you use UUIDs in your GRUB menu.lst, instead of device nodes, as I explained in my first post in this thread, you will get around the issue of the BIOS and the kernel ordering the devices differently. That's part of the reason for UUIDs, universal unique identifier.

---

### Post by manij on 2008-12-02
> **gTinker said:**
> If you use UUIDs in your GRUB menu.lst, instead of device nodes, as I explained in my first post in this thread, you will get around the issue of the BIOS and the kernel ordering the devices differently. That's part of the reason for UUIDs, universal unique identifier.

Thanks gTinker. I tried this and works. I found Super grub disk to be easier solution. It pointed to the menu.lst in the new installation. I was curious more baout the inner workings and understand why the bios and fdisk -l look at thing differently.

---

### Post by manij on 2008-12-02
> **gTinker said:**
> If you use UUIDs in your GRUB menu.lst, instead of device nodes, as I explained in my first post in this thread, you will get around the issue of the BIOS and the kernel ordering the devices differently. That's part of the reason for UUIDs, universal unique identifier.

Thanks gTinker. I tried this and works. I found Super grub disk to be easier solution. It pointed to the menu.lst in the new installation. I was curious more baout the inner workings and understand why the bios and fdisk -l look at thing differently.

---

### Post by gTinker on 2008-12-03
[QUOTE=manij] I was curious more baout the inner workings and understand why the bios and fdisk -l look at thing differently.[/QUOTE]

It's really a question of the BIOS and the kernel enumerating the devices differently. It started happening back somewhere around the 2.6.18 kernel, if I remember correctly. Naturally, since the system is up when you issue the command fdisk -l, it gives you the info as the kernel sees it.

---

