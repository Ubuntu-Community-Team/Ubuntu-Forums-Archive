---
title: "Configuring GRUB to load Vista"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by lapp on 2008-12-16
Hi there.

I recently installed Intrepid 8.1 on my PC. I have sorted through an truckload of issues over the past week getting different bits and pieces working and i am so very close to just breaking down and giving up. There is one issue that i am having no success with and i really just need some help. All i want to do is have GRUB boot my Vista.

Please keep in mind that i am relatively new to Linux.

Before i go any further my setup is as follows;

All my hard drives are SATA / AHCI

Disk 0 is Windows Vista (37GB WD Raptor)
Disk 1 is Linux Ubuntu 8.1 (37 GB Raptor)
Disk 2 is FAT32 Storage (120GB Seagate)
Disk 3 is NTFS Storage (320 WD)


SUDO FDISK -l


```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91737343

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4501    36148224    7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73262b8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4310    34620043+  83  Linux
/dev/sdb2            4311        4500     1526175    5  Extended
/dev/sdb5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cdb4cdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    b  W95 FAT32

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xece71d8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      620177   312569176+   7  HPFS/NTFS

```


Firstly i installed Vista. Secondly i installed Ubuntu - telling GRUB to install to Disk 1 so it wouldn't mess with my Vista MBR. 

-Windows boots just fine if i set Disk 0 as the first drive to boot in BIOS.
-Ubuntu boots just find if i set Disk 1 as the first drive to boot in BIOS.

Having to switch the primary boot drive isn't the most elegant solution though, so i want to be able to select which OS to boot using GRUB. Now there is definitely an entry to boot Vista from within GRUB, but it doesn't work. It gives the following error;

Error 13: Invalid or unsupported executable format

I'm surprised GRUB can even see Vista which is sitting entirely on another hard drive.


The contents of my grub menu.lst file are as follows;
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
# kopt=root=UUID=15b48504-d87b-4670-a84a-7922b56eef14 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=15b48504-d87b-4670-a84a-7922b56eef14

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		15b48504-d87b-4670-a84a-7922b56eef14
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=15b48504-d87b-4670-a84a-7922b56eef14 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		15b48504-d87b-4670-a84a-7922b56eef14
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=15b48504-d87b-4670-a84a-7922b56eef14 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		15b48504-d87b-4670-a84a-7922b56eef14
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=15b48504-d87b-4670-a84a-7922b56eef14 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		15b48504-d87b-4670-a84a-7922b56eef14
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=15b48504-d87b-4670-a84a-7922b56eef14 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		15b48504-d87b-4670-a84a-7922b56eef14
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


```

There is also a file in my /boot/grub directory called menu.1st

It's contents are as follows;

```

title              Windows XP
root               (sd0,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

I edited the root line from (hd1,0) to (sd0,0) but it made no difference.


Can anyone see where i have gone wrong? I'm so close to getting everything working properly. I'm tired and i really need some help :(

---

### Post by Mark Phelps on 2008-12-16
Since you can boot Ubuntu from your second drive, change (hd0,0) to (hd1,0) in your menu.lst entry for Vista.  Also is a good idea to change "root" on the same stanza to "rootnoverify".

---

### Post by caljohnsmith on 2008-12-16
How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Vista entry to the following entries:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title       Windows Vista (hd3)
rootnoverify     (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
Based on the info you gave, one of those entries above should work to boot Vista. If not, let me know exactly what happens when you try each one from the Grub menu.

---

### Post by lapp on 2008-12-16
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```

This entry hands me off to the Vista bootloader. Both OS's will boot cleanly through GRUB now.

You guys are outstanding and have saved me another huge headache! Thanks lot :)

---

### Post by caljohnsmith on 2008-12-16
Glad to hear one of those entries worked; cheers and have fun with Vista and Ubuntu. :)

---

