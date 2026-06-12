---
title: "Just installed Ubuntu 8.10 - dual boot GRUB issue"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by awilki01 on 2009-02-12
Hello everyone.  I just did a clean install of 8.10.  Everything is working great with the exception of GRUB.  GRUB set up the parameters for my Windows XP drive incorrectly.  When I make that drive the boot drive in BIOS, it boots XP just fine.  However, when I make my Ubuntu drive the boot partition, GRUB loads fine, and I can boot Ubuntu, but when selecting Windows XP, I get an error.

Here are some outputs to help you help me figure this out....
/dev/sda is my Windows XP drive
/dev/sdb is my Ubuntu drive
/dev/sdc is about to be reformatted - had tried SUSE 11.1

Grub's device.map:
> 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


fdisk -l:
> 
Disk /dev/sda: 400.0 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17752   134205088+   7  HPFS/NTFS
/dev/sda2           17753       51681   256503240    f  W95 Ext'd (LBA)
/dev/sda5           17753       51681   256503208+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c056bda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       58570   470463493+  83  Linux
/dev/sdb2           58571       60801    17920507+   5  Extended
/dev/sdb5           58571       60801    17920476   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a923a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9485    76188231    7  HPFS/NTFS
/dev/sdc2            9486       14462    39977752+  83  Linux


Grub's menu.lst:
> 
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
# kopt=root=UUID=f5a9f585-6e50-4970-8837-183ca2a6160d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f5a9f585-6e50-4970-8837-183ca2a6160d

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f5a9f585-6e50-4970-8837-183ca2a6160d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f5a9f585-6e50-4970-883
7-183ca2a6160d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f5a9f585-6e50-4970-8837-183ca2a6160d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f5a9f585-6e50-4970-883
7-183ca2a6160d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f5a9f585-6e50-4970-8837-183ca2a6160d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f5a9f585-6e50-4970-8837
-183ca2a6160d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f5a9f585-6e50-4970-8837-183ca2a6160d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f5a9f585-6e50-4970-8837
-183ca2a6160d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f5a9f585-6e50-4970-8837-183ca2a6160d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		openSUSE 11.1 (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz root=/dev/disk/by-id/ata-WDC_WD1200JB-00CRA1_WD-WM
A8C2012195-part2 resume=/dev/disk/by-id/ata-WDC_WD1200JB-00CRA1_WD-WMA8C2012195-
part3 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Failsafe -- openSUSE 11.1 (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz root=/dev/disk/by-id/ata-WDC_WD1200JB-00CRA1_WD-WM
A8C2012195-part2 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz
=off highres=off processor.max_cstate=1 x11failsafe 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Kernel-2.6.27.7-9-default (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-WDC_WD
1200JB-00CRA1_WD-WMA8C2012195-part2 resume=/dev/disk/by-id/ata-WDC_WD1200JB-00CR
A1_WD-WMA8C2012195-part3 splash=silent showopts 
initrd		/boot/initrd-2.6.27.7-9-default
savedefault
boot


---

### Post by caljohnsmith on 2009-02-12
How about trying the following two entries in your menu.lst:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Let me know if one of those works, and if not, what happens when you try them from the Grub menu. We can work from there if necessary.

---

### Post by awilki01 on 2009-02-12
Your second entry was the key!  Thanks so much!  

I am confused on how that worked though being that Grub's device.map shows my WinXP drive as hd0.  It probably stems from my lack of understanding of the maps you have configured.

---

### Post by caljohnsmith on 2009-02-12
Grub's device.map file is mostly useless, it is only used if your menu.lst has any references to "sda" or "hda" type devices so Grub can translate those into the BIOS boot drives (hdX). The confusion about how the drives are numbered I think is because on start up, Grub sees the order of drives as the BIOS boot order, not how the drives are ordered as sda, sdb, sdc, etc in Ubuntu. So if for example you boot your sdb drive first on start up, it is then (hd0), and your sda and sdc drives would have to be (hd1) and (hd2); but which one is which is determined again by your BIOS boot order. Anyway, glad one of those entries worked; cheers and enjoy Ubuntu and Windows. :)

---

### Post by awilki01 on 2009-02-15
That actually makes sense.  Thanks so much for taking the time to explain.  Have a great day!

---

