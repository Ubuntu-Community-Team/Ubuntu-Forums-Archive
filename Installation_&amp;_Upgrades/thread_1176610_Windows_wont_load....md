---
title: "Windows wont load..."
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by fellixombc on 2009-06-02
After I gladly installed ubuntu to dual boot xp and ubuntu, i got an error.
I would like to use the GRUB loader to load xp, but I need your help.


I don't know which disk or partion my xp is on. But, I know the type of drive its on, NTFS (I'm pretty sure because FAT32 system saving or w/e is the drive I installed ubuntu on.).

Here is my GRUB loader: 
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0B28-1607 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0B28-1607 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0B28-1607 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

and my fdisk:
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc933c933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66236623

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4658    37415353+   7  HPFS/NTFS
/dev/sdb2            4659        4863     1646662+   5  Extended
/dev/sdb5            4659        4863     1646631   82  Linux swap / Solaris

```

And, if needed, the boot.ini file in the correct file directory.
```
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect

c:\wubildr.mbr="Ubuntu"
```

Thank you

Sorry about double posting, was in a rush, and selected kubuntu by accident, i need help with ubuntu.

---

### Post by UrbenLegend on 2009-06-02
What is the error that you get exactly? Does it say anything when it boots up?

I am kind of in a rush right now, but from what I can gather:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

should have 'rootnoverify' instead of 'root'. Try changing that first and report back.

I also highly recommend that you install linux into an ext3 partition rather than a fat32, but we can deal with that later.

---

### Post by fellixombc on 2009-06-02
> **UrbenLegend said:**
> What is the error that you get exactly? Does it say anything when it boots up?

I am kind of in a rush right now, but from what I can gather:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

should have 'rootnoverify' instead of 'root'. Try changing that first and report back.

I also highly recommend that you install linux into an ext3 partition rather than a fat32, but we can deal with that later.
Alright, I selected windows, and a bunch of options camp up from boot.ini, i selected windows xp, and it said something like "the file path cannot be found, your computer path"
^ something like that.

Do i need to edit anything in boot.ini ?

---

### Post by UrbenLegend on 2009-06-02
No you do not need to edit anything in boot.ini.

Change 'root' to 'rootnoverify' in your Windows XP Professional entry. Also get rid of the two map statements completely.

---

### Post by fellixombc on 2009-06-02
> **UrbenLegend said:**
> No you do not need to edit anything in boot.ini.

Change 'root' to 'rootnoverify' in your Windows XP Professional entry. Also get rid of the two map statements completely.

Alright I did, and when i did, he just gave me 11 and a black happy smile.
like: '11:D'

this is my code..```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
savedefault
chainloader	+1
```


and when I moved my key, it just brought me to my "broken" menu, it tries starting a deleted/formatted windows in the broken menu..

---

### Post by Mark Phelps on 2009-06-02
From my experience, in a two drive system, the active boot drive is (0), in GRUB terms, and the other drive is (1).

So, given that he apparently has two MS Windows OSs, each on a different drive, one has to be (hd0,0) while the other has to be (hd1,0).

Since he's booting from the XP drive, that is (hd0,0) and no map statements are needed. But to boot into Windows NT, that would be (hd1,0) and the map statements would be needed.

So ... switch the two title rows in the original menu.lst for the MS Windows OSs and change root to rootnoverify they should work OK.

---

### Post by fellixombc on 2009-06-02
> **Mark Phelps said:**
> From my experience, in a two drive system, the active boot drive is (0), in GRUB terms, and the other drive is (1).

So, given that he apparently has two MS Windows OSs, each on a different drive, one has to be (hd0,0) while the other has to be (hd1,0).

Since he's booting from the XP drive, that is (hd0,0) and no map statements are needed. But to boot into Windows NT, that would be (hd1,0) and the map statements would be needed.

So ... switch the two title rows in the original menu.lst for the MS Windows OSs and change root to rootnoverify they should work OK.

So it would be: ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
savedefault
chainloader	+1
```

correct?

---

### Post by fellixombc on 2009-06-02
didn't work, just brought me to the broken menu, and the windows file are located in Media hard drive.

---

### Post by Mark Phelps on 2009-06-02
OK, now that I look back at your postings, I see a reference for wubildr -- the Wubi loader.  This implies that you installed Ubuntu INSIDE XP, not as a separate partition.

I have no real familiarity with Wubi, so I can't recommend anything specific and would be surprised if you could use GRUB in that case to boot MS Windows.  The more likely scenario is that you select Ubuntu from the MS Windows loader menu, not the other way around.

And, please don't PM me for support.

---

### Post by fellixombc on 2009-06-02
[IMG]http://img192.imageshack.us/img192/8960/imagey.png[/IMG]
^ if this helps anyone.


oh i c, sorry about the PM, I just needed an answer =/

---

### Post by UrbenLegend on 2009-06-13
O_o looks like a Linux install from hell! Where is your root directory? Can you run it through GParted?

---

