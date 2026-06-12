---
title: "Mounting USB floppy drive"
date: 2011-02-15
forum: Hardware
---

### Post by cafink on 2011-02-15
I have a Bytecc BT-144 USB floppy drive.  Normally, when I insert a CD-ROM, or a USB device, it is automatically mounted, and an icon appears on the desktop.  But when I connect the BT-144, the drive starts making a lot of noise, like it's continually trying to access the disk.  This stops if I insert a disk, but I still can't find a way to access the contents of the disk.

A "Floppy Drive" entry appears in Places > Computer, but nothing happens when I double-click it or right-click it and select "open."

"sudo fdisk -l" doesn't appear to reveal anything useful:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76063   610967552   83  Linux
/dev/sda2           76063       77826    14161921    5  Extended
/dev/sda5           76063       77826    14161920   82  Linux swap / Solaris

```

I can see the floppy drive listed if I run "lsusb":

```

Bus 003 Device 003: ID 0644:0000 TEAC Corp. Floppy

```

...but I don't know what to do from there.

How can I access this floppy drive in Ubuntu (I'm using 10.10, specifically)?

Thanks.

---

### Post by jerrrys on 2011-02-16
could this be the problem ?

[ATTACH]183644[/ATTACH]

havent really looked, but maybe a answer here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=floppy&as_qdr=all&sa=Google+Search&lang=en#878](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=floppy&as_qdr=all&sa=Google+Search&lang=en#878)

---

