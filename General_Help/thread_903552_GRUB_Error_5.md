---
title: "GRUB Error 5"
date: 2008-08-28
forum: General Help
---

### Post by Lexicon101 on 2008-08-28
Ok... Just tried installing intrepid ibex alpha 4 on the second partition of an external HD.. Now when I boot up, I get this error. I'm running the livecd from the installation right now..
I've tried posting fdisk -l results, but it seems to crash if I try to highlight something. Anyway, it's all kind of a pain. It's happened twice, same scenario, except I've tried deleting the partition myself and having it as free space, only letting the installation disk use the free space already there..
Anyway, here's my configuration:
DISK 1:
Partition 1: ubuntu 8.04
Partition 2: windows XP
Partition 3: Linux swap
DISK 2:
Partition 1: Ext3 file space
Partition 2: Ext3 ibex installation
Partition 3: Linux swap

(I'll take a SS of my terminal output and manually copy it..)

---

### Post by Lexicon101 on 2008-08-29
> **Lexicon101 said:**
> Ok... Just tried installing intrepid ibex alpha 4 on the second partition of an external HD.. Now when I boot up, I get this error. I'm running the livecd from the installation right now..
I've tried posting fdisk -l results, but it seems to crash if I try to highlight something. Anyway, it's all kind of a pain. It's happened twice, same scenario, except I've tried deleting the partition myself and having it as free space, only letting the installation disk use the free space already there..
Anyway, here's my configuration:
DISK 1:
Partition 1: ubuntu 8.04
Partition 2: windows XP
Partition 3: Linux swap
DISK 2:
Partition 1: Ext3 file space
Partition 2: Ext3 ibex installation
Partition 3: Linux swap

(I'll take a SS of my terminal output and manually copy it..)

Well, this is after me messing with it.. like.. a lot, but the problem persists, so here's the fdisk output;

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x497abe0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5391    43303176   83  Linux
/dev/sda2   *        5392        9327    31615920    7  HPFS/NTFS
/dev/sda3            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24994   200764273+  83  Linux
/dev/sdb2   *       24995       30174    41608318+  83  Linux
/dev/sdb3           30175       30401     1823377+   f  W95 Ext'd (LBA)
/dev/sdb5           30175       30401     1823346   82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2008-08-29
Do you know for sure which HDD you are booting at start up? Is it the 80 GB or the 250 GB? Also please post your /boot/grub/menu.lst from whichever HDD you are booting.

---

### Post by Lexicon101 on 2008-08-29
I know for sure I'm booting from the 80 GB. I'll post the grub list...
I basically copied over settings from the new installation into the old menu.lst..
>.O
The annoying thing is, it isn't a partitioning error as far as I know.. I let the disk partition it itself (didn't work). I formatted it with GParted LiveCD.. (didn't work)
It seems to be a problem with the installation, it doesn't seem like it'd have anything to do with it being 64-bit. The Ubuntu LiveCD works fine, but from looking around on google and ubuntuforums, it seems grub or gparted has a problem with external HDs with multible partitions.. But I can't find any kind of actual solution.. The only thing I can think of (which I'm about to try if this doesn't get any hits) is moving the media partition to the right, then making the boot partition the first one on the disk. I'd have to update the menu.lst, and a few other things, but.. Well, I'll try if I don't get an answer here.

---

### Post by Lexicon101 on 2008-08-30
> **Lexicon101 said:**
> I know for sure I'm booting from the 80 GB. I'll post the grub list...
I basically copied over settings from the new installation into the old menu.lst..
>.O
The annoying thing is, it isn't a partitioning error as far as I know.. I let the disk partition it itself (didn't work). I formatted it with GParted LiveCD.. (didn't work)
It seems to be a problem with the installation, it doesn't seem like it'd have anything to do with it being 64-bit. The Ubuntu LiveCD works fine, but from looking around on google and ubuntuforums, it seems grub or gparted has a problem with external HDs with multible partitions.. But I can't find any kind of actual solution.. The only thing I can think of (which I'm about to try if this doesn't get any hits) is moving the media partition to the right, then making the boot partition the first one on the disk. I'd have to update the menu.lst, and a few other things, but.. Well, I'll try if I don't get an answer here.

Ok, Here's the list file.


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
#hiddenmenusearch archives

# Pretty colours
color light-gray/black black/light-gray

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/grub_skull.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=5cda37ee-90db-40dd-9163-c99d0d93c6aa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash vga=786

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
# howmany=1

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5cda37ee-90db-40dd-9163-c99d0d93c6aa ro quiet vga=791
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5cda37ee-90db-40dd-9163-c99d0d93c6aa ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=04fa1a16-3c0c-4830-a54e-baca741fb4ec ro quiet splash 
initrd		/boot/initrd.img-2.6.26-5-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=04fa1a16-3c0c-4830-a54e-baca741fb4ec ro  single
initrd		/boot/initrd.img-2.6.26-5-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd1,4)
kernel		/boot/last-good-boot/vmlinuz root=UUID=04fa1a16-3c0c-4830-a54e-baca741fb4ec ro quiet splash  last-good-boot
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
rootnoverify	(hd0,1)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by caljohnsmith on 2008-08-30
> **Lexicon101 said:**
> 
```

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic
root		[COLOR="Red"](hd1,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=04fa1a16-3c0c-4830-a54e-baca741fb4ec ro quiet splash 
initrd		/boot/initrd.img-2.6.26-5-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic (recovery mode)
root		[COLOR="Red"](hd1,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=04fa1a16-3c0c-4830-a54e-baca741fb4ec ro  single
initrd		/boot/initrd.img-2.6.26-5-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		[COLOR="Red"](hd1,4)[/COLOR]
kernel		/boot/last-good-boot/vmlinuz root=UUID=04fa1a16-3c0c-4830-a54e-baca741fb4ec ro quiet splash  last-good-boot
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		[COLOR="Red"](hd1,4)[/COLOR]
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
rootnoverify	(hd0,1)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```
(hd1,4) would be sdb5, which is your swap partition according to fdisk. Try changing (hd1,4) to (hd1,1) since sdb2 is your Linux partition that is marked as bootable. If that doesn't work the only other place Intrepid could be is on (hd1,0) according to fdisk, so you could try that. But I'll bet (hd1,1) is correct.

---

### Post by Lexicon101 on 2008-09-24
Meh. I worked around it. First, moving it forward to the first partition on the drive, then just moving it to the first drive, leaving the backup on the external... Anyway, intrepid isn't good yet on a usb drive. USB controllers or something go down, and it crashes the whole system. Really freaked me out the first time. Anyway, thanks for the help..

---

