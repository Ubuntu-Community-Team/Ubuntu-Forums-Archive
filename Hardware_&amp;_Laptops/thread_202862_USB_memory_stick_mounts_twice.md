---
title: "USB memory stick mounts twice"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by chestnut1969 on 2006-06-24
Hello

Whenever I insert a USB memory stick (LEXMEDIA) into my laptop or desktop running Dapper, two icons appear for the device on the desktop. One is labelled 'LEXMEDIA', and opens showing drive contents correctly, the other icon is labelled 'usbdisk', and when open displays window showing numerous files with garbaged names.

My laptop was running Ubunut Dapper test (upgraded from 5.10), and never used to have this problem until the last week of Dapper testing updates.

My desktop is a clean install of Ubuntu Dapper (final), and has always had this issue.

Any ideas appreciated on how to fix this?

This is an extract from a rather large dmesg output:
 
[4305596.758000] attempt to access beyond end of device
[4305596.758000] sda: rw=0, want=535823375, limit=1014784
[4305596.758000] attempt to access beyond end of device
[4305596.758000] sda: rw=0, want=535823374, limit=1014784
[4305596.758000] attempt to access beyond end of device
[4305596.758000] sda: rw=0, want=535823375, limit=1014784

lsusb displays:

Bus 001 Device 003: ID 05dc:a410 Lexar Media, Inc.
Bus 001 Device 001: ID 0000:0000



Many thanks

---

### Post by chestnut1969 on 2006-06-28
Just to add

The USB stick works without problem on Fedora Core 5 & SUSE 10.1

---

### Post by chestnut1969 on 2006-07-17
Well, I have found a solution (not too sure why this works!!)

I reformatted USB stick to NTFS, now mounts OK in Debian SID & Ubuntu. For whatever reason the Debian based distros were just not happy with the FAT32 formatted stick...

cheers

---

