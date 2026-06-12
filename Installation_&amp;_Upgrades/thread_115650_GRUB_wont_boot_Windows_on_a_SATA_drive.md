---
title: "GRUB wont boot Windows on a SATA drive"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by three_sixteen on 2006-01-11
So I've installed Ubuntu on a computer with two hard drives.

GRUB sees the Ubuntu installation and boots fine, but dosen't list Windows which is on a seperate SATA drive.

Heres what I got.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/sda1 	/media/windows  ntfs    nls=utf8,umask=0222 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

```
nick@ubuntu:/etc$ sudo fdisk -l

Disk /dev/hdd: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2395    19237806   83  Linux
/dev/hdd2            2396        2501      851445    5  Extended
/dev/hdd5            2396        2501      851413+  82  Linux swap / Solaris

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10010    80405293+   7  HPFS/NTFS

```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdd1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img,-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest8,6+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

title 		Microsoft Windows
root 		(sd0,1)
chainloader+1
### END DEBIAN AUTOMAGIC KERNELS LIST

```

As you can see I tried to add a Windows line, but it dosen't work.  I'm not sure where I've gone wrong.  sda1 is the drive I'm trying to boot off of.

---

### Post by three_sixteen on 2006-01-11
Well, I got it to dual boot.. sort of..

I had to remap the drives in GRUB to get it to boot, but when it went to the windows partition to boot it the NTLDR file turned up missing.

Awesome.

---

### Post by DoorGunner on 2006-01-11
what you need to do is modify your grub

title Windows 
rootnoverify (sd0,0)
chainloader+1

You have this line
/dev/sda1               1       10010    80405293+   7  HPFS/NTFS
remember that you have to subtract 1 from everything in your grub. Windows is on partition 1.
grub sd0,0  translated means your first sata drive, first partition

---

### Post by Kipper on 2006-01-11
Soory Doorgunner, but sd0 is wrong! 

GRUB makes no distinction between PATA, SATA and SCSI drives. As far as it is concerned it just enumerates the hard drives it finds in their boot order, hd0, hd1 etc.

In addition, if the drive /dev/hdd is the first boot device and /dev/sda is the second, and Windows is intalled on the SATA drive, you cannot boot it from the first drive with GRUB without using the "map" command. 

The windows entry should be:

title Windows XP
rootnoverify (hd1,0)
hide (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by DoorGunner on 2006-01-11
i was just looking at the partition aspect.....

> In addition, if the drive /dev/hdd is the first boot device and /dev/sda is the second, and Windows is intalled on the SATA drive, you cannot boot it from the first drive with GRUB without using the "map" command.
I was wondering how he had hd and sd on the same machine :???:

---

### Post by three_sixteen on 2006-01-11
[QUOTE=Kipper]Soory Doorgunner, but sd0 is wrong! 

GRUB makes no distinction between PATA, SATA and SCSI drives. As far as it is concerned it just enumerates the hard drives it finds in their boot order, hd0, hd1 etc.

In addition, if the drive /dev/hdd is the first boot device and /dev/sda is the second, and Windows is intalled on the SATA drive, you cannot boot it from the first drive with GRUB without using the "map" command. 

The windows entry should be:

title Windows XP
rootnoverify (hd1,0)
hide (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1[/QUOTE]

This is just about what I ended up doing to get it to go.  It would have worked too if not for the damn NTLDR error :mad:

---

