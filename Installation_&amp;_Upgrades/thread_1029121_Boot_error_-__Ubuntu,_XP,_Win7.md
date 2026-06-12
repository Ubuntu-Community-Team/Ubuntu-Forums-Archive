---
title: "Boot error -  Ubuntu, XP, Win7"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by civhero on 2009-01-03
I recently installed the Windows 7 beta to a separate hard drive than my primary hard drive with Ubuntu 8.1 and XP.  In the process, Windows 7 did something to my grub setting for XP.  I can still see the XP partition on the drive, but it won't boot if I select the Windows Vista/Longhorn loader.  I don't know what to edit in the menu.lst to get things back to normal.  


Here is my fdisk-l.  XP is sdb1.  Windows7 is sde1 (I believe). 


Disk /dev/sda: 1500.3 GB, 1500300828160 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930275055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64ada363

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  2930272064  1465136001    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268414019   134206978+   7  HPFS/NTFS
/dev/sdb2       268414020   625137344   178361662+   5  Extended
/dev/sdb5       268414083   600445439   166015678+  83  Linux
/dev/sdb6       600445503   625137344    12345921   82  Linux swap / Solaris

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb5ccb5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           16065  1465144064   732564000    f  W95 Ext'd (LBA)
/dev/sdc5           16128  1465144064   732563968+   7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xccf4bfbe

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43f143f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048   234388349   117193151    7  HPFS/NTFS


Here is the grub menu:

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
# kopt=root=UUID=4e77f29e-96a9-41b4-80b5-72f9b4156adc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4e77f29e-96a9-41b4-80b5-72f9b4156adc

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
uuid		4e77f29e-96a9-41b4-80b5-72f9b4156adc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4e77f29e-96a9-41b4-80b5-72f9b4156adc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4e77f29e-96a9-41b4-80b5-72f9b4156adc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4e77f29e-96a9-41b4-80b5-72f9b4156adc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4e77f29e-96a9-41b4-80b5-72f9b4156adc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

How can I tell what hdx,y corresponds to hdb1 (XP), and will changing the last entry from hd1,0 to hdx,y fix things?  

Thanks in advance.

---

### Post by logos34 on 2009-01-03
It appears Grub bootloader (stage1) is on another disk (sda ?).

Here's what I suggest you do:

(re)write grub to the mbr of sdb:

**sudo grub-install /dev/sdb**

edit windows entry:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

reboot, enter the Bios and set sdb first in the hard disk boot priority

now you should be able to boot xp on the same disk.  

Windows 7 may not be so easy...Is that a RAID0 array (2x250GB)?  Sde not flagged boot (*) either

---

