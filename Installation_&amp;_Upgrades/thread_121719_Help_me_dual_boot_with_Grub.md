---
title: "Help me dual boot with Grub"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by Oren on 2006-01-25
Hi all 

I wonder if someone can give me a hand with this.
I have Windows XP pro installed on a SATA drive.
I have installed Ubuntu (5.10) on an IDE master and used Grub as the boot loader.

On reboot I got the menu alright but when I try to boot into windows I get a message telling me that the FS is FAT and this is not a bootable disk :confused: 

This is the menu entry as it is written in Grub's menu list:
> title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Something's not right, right? So, good people, what do I need to do to convince Grub that the disk is indeed NTFS and that there really is a an MBR there :smile: 

Any help will be appreciated.

---

### Post by Sutekh on 2006-01-25
Whats the output of
```
cat /boot/grub/device.map
```
and
```
sudo fdisk -l
```

---

### Post by Oren on 2006-01-26
[QUOTE=Sutekh]Whats the output of
```
cat /boot/grub/device.map
```[/QUOTE]

[COLOR="Blue"](hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
[/COLOR]

and
> ```
sudo fdisk -l
```

[COLOR="Blue"]Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        2434    19302097+   5  Extended
/dev/hda5              32        2434    19302066   8e  Linux LVM

Disk /dev/hdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1826    14667313+   c  W95 FAT32 (LBA)

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3122    25077433+   7  HPFS/NTFS
/dev/sda2            3123       14596    92164905    7  HPFS/NTFS
[/COLOR]

Thanks for having a look.
P.S. the FAT32 is a spare drive and is a slave on the primary IDE.

---

### Post by lha on 2006-01-26
Looks like grub sees sda as (hd1) and not (hd2) as your device.map says. You can confirm this if you press 'c' in in grub menu to open command line. Try to type
```
cat (hd0
```
and press <tab>. Grub lists all partitions on (hd0)
Use backspace to remove '0' and replace it with 1 and press tab again. Do the same after replacing '1' with '2'.

---

### Post by Sutekh on 2006-01-26
```

sudo fdisk -l

...
Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3122    25077433+   7  HPFS/NTFS
/dev/sda2            3123       14596    92164905    7  HPFS/NTFS
...

```
So sda1 is the windows partition (and is bootable)
```

cat /boot/grub/device.map

...
(hd2)   /dev/sda
...

```
And sda is mapped to hd2.
```

cat /boot/grub/menu.lst

...
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
...

```
And the root (hd2,0) is correct too.

For the life of me this looks correct.

Only thing I can suggest is to comment the 
```

map (hd0) (hd2)
map (hd2) (hd0)

```
You usually need this to trick windows into thinking its on the first partition of a disc.  Seeing as it has a disc to itself, maybe this is uneccessary

---

