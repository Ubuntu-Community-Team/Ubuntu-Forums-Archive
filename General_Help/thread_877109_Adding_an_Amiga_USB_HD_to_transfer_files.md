---
title: "Adding an Amiga USB HD to transfer files"
date: 2008-08-01
forum: General Help
---

### Post by Voorhees1979 on 2008-08-01
Hi all

I am trying to add my Amiga hd into a usb cradle and mounting it via usb to ubuntu to transfer some files to it but am running into some problems.

From this link [https://help.ubuntu.com/community/EUAEAmigaEmulator](https://help.ubuntu.com/community/EUAEAmigaEmulator)

It says I can just plug in the hd and Ubuntu will pick it up but its not.

It I type lsusb:
joe@joe-desktop:~$ lsusb
Bus 003 Device 006: ID 05ab:0060 In-System Design USB 2.0 ATA Bridge
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000  

Its not listed.

If I type fdisk -l:

Disk /dev/sdd: 4871 MB, 4871301120 bytes
150 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 9300 * 512 = 4761600 bytes
Disk identifier: 0x00000000

There it is.

So I made a mount point called /media/external and then tried this

sudo mount -t affs /dev/sdd /media/external

mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Anyone have any ideas pls?

Of course I tried loading uae on ubuntu but I cant mount the hd to even be seen in there.

Many thanks

---

