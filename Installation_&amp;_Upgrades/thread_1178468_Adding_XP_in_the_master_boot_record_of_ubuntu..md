---
title: "Adding XP in the master boot record of ubuntu."
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by kapil naudiyal on 2009-06-04
I have 2 hard drives one with XP and one with Ubuntu.

As per Bios XP hard drive is First Primary Master and Ubuntu drive is Third primary master. 

O/p of the 'fdisk -lu' is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x218f218e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b783b77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   195527114    97763526   83  Linux
/dev/sdb2       195527115   297090044    50781465    5  Extended
/dev/sdb5       195527178   295130114    49801468+  83  Linux
/dev/sdb6       295130178   297090044      979933+  82  Linux swap / Solaris

Entries in my /boot/grub/menu.lst file are:

title              Windows XP
root               (hd0,0)
savedefault
makeactive
chainloader        +1


My problem is that when i select the XP option in boot sequence, I get 'invalid or unsupported exception'

Can someone guide me to properly sequence the entries so that i can boot from XP as well as ubuntu.

Thanks 
Kapil

---

### Post by confused57 on 2009-06-04
Boot into Ubuntu, open a terminal, post the output of:
```
gedit /boot/grub/device.map
```

then:
```
sudo grub
find /boot/grub/stage1
quit
```
post the output of "find /boot/grub/stage1", the command 
"quit", just exits from the grub prompt.

This may help to determine the grub entry needed for XP?

---

### Post by kapil naudiyal on 2009-06-05
output of 

gedit /boot/grub/device.map

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc




output of 

find /boot/grub/stage1

(hd1,0)

---

### Post by kapil naudiyal on 2009-06-05
> **confused57 said:**
> Boot into Ubuntu, open a terminal, post the output of:
```
gedit /boot/grub/device.map
```then:
```
sudo grub
find /boot/grub/stage1
quit
```post the output of "find /boot/grub/stage1", the command 
"quit", just exits from the grub prompt.

This may help to determine the grub entry needed for XP?


		output of 

gedit /boot/grub/device.map

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc




output of 

find /boot/grub/stage1

(hd1,0)

---

### Post by confused57 on 2009-06-05
Your Windows grub entry looks like it "should" work, but you might try copying & pasting this entry into your menu.lst:
```
title   Windows XP  Alternate Entry
rootnoverify  (hd0,0)
makeactive
chainloader +1
```

If this doesn't work, you might want to download and make a copy of Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You can try to boot Windows with SGD, or you can restore Window's IPL to the mbr.

There are other options for setting up a dual-boot with 2 hard drives, if the above doesn't work.

---

### Post by presence1960 on 2009-06-05
Try this, you need map lines in the windows entry. 

```
title        Windows XP
rootnoverify (hd0,0)
map          (hd0) (hd1)
map          (hd1) (hd0)
chainloader  +1
```

---

