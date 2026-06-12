---
title: "Not recognizing new SCSI drives - Ubuntu 12.04 Server"
date: 2014-03-21
forum: Hardware
---

### Post by reach-the-pharcide on 2014-03-21
[COLOR=#333333]Linux newbie here.[/COLOR]

[COLOR=#333333]I have a HP Proliant Server, which I can get details on if they will help. This blade has been running Windows server 2008 up until last week, when I loaded Ubuntu 12.04 server to implement a FOG server for imaging.[/COLOR]

[COLOR=#333333]I started with a 148GB SCSI drive and installed Ubuntu, got the fog working wonderfully. I decided today that I needed more space for images. There are three 72GB SCSI drives sitting in the server (unseated) and I want to do a RAID 5 with them. I pushed all three of the drives in, did several restarts, but still[/COLOR][COLOR=#333333]
```
fdisk -l
```[/COLOR]
[COLOR=#333333]and[/COLOR][COLOR=#333333]
```
parted -l
```[/COLOR]
[COLOR=#333333]do not see them.[/COLOR]
[COLOR=#333333]
```
/dev/cciss/c0d0
```[/COLOR]
[COLOR=#333333]exists, but
[/COLOR][COLOR=#333333]```
c0d1
```[/COLOR]
[COLOR=#333333]and so forth do not.[/COLOR]

[COLOR=#333333]Am I missing something here? The drives worked fine a week ago in a Windows environment.[/COLOR]

[COLOR=#333333]Thanks so much for any help you can provide.[/COLOR]

[COLOR=#333333]For more info: Here is the readout of fdisk -l:[/COLOR]
[COLOR=#333333]
```
root@S-9782:~# fdisk -l

Disk /dev/cciss/c0d0: 146.8 GB, 146778685440 bytes
255 heads, 32 sectors/track, 35132 cylinders, total 286677120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fd38

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *        2048      499711      248832   83  Linux
/dev/cciss/c0d0p2          501758   286676991   143087617    5  Extended
/dev/cciss/c0d0p5          501760   286676991   143087616   8e  Linux LVM

Disk /dev/mapper/S--9782--vg-root: 137.9 GB, 137912909824 bytes
255 heads, 63 sectors/track, 16766 cylinders, total 269361152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/S--9782--vg-root doesn't contain a valid partition table

Disk /dev/mapper/S--9782--vg-swap_1: 8585 MB, 8585740288 bytes
255 heads, 63 sectors/track, 1043 cylinders, total 16769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/S--9782--vg-swap_1 doesn't contain a valid partition table
```[/COLOR]

---

### Post by reach-the-pharcide on 2014-03-25
Anyone have any clue what is going on here?

---

### Post by reach-the-pharcide on 2014-03-26
I figured this out.  Just for posterity sake, I used this resource:


[http://www.scottalanmiller.com/linux/2012/04/22/adding-new-drives-to-an-hp-proliant-smartarray-with-lvm/](http://www.scottalanmiller.com/linux/2012/04/22/adding-new-drives-to-an-hp-proliant-smartarray-with-lvm/)


Essentially I was missing the HPACUCLI utility that is needed to pass logical drives through to the LVM.  The controller saw them, it just was not passing them through to linux.  Pretty easy fix, getting the HP repository to load was a little annoying.

---

