---
title: "Problem with GrUB"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by aeronotix on 2009-01-12
I was installing Xubuntu on a friends hard drive and I disconnected my internal HDD to save me doing anything accidentally to it because when I boot Xubuntu on this monitor all the fonts are really small, but I know the install off by heart nearly (it's pretty much next, next, next for a full install) 

Anyway, after doing that I plug my drive back in and get a message in German which I presume to be Hard Disk Error, since this is an Acer PC I have messed up in similar ways before and this is what it says, except it is in German for some reason. 

My guess is that I messed up the GrUB MBR and needed to re-install it.

So I boot into the Xubuntu LiveCD and open a terminal. and do the following
```
sudo grub
```

```
find /boot/grub/stage1
```

Which returns (hd0,5)

```
root (hd0,5)
```

```
setup (hd0,5)
```

And hey presto it should be done, right? WRONG. It gives me the same error. I think I should translate the German (If anyone gives me a reason why it's in German they get a cookie) but I'm so sure the MBR is what's to blame here.

I can boot into my usual Ubuntu install by choosing boot from first hard disk on the Xubuntu LiveCD menu but as for letting the start up go for itself it halts at Ze German part. Any ideas?

---

### Post by aeronotix on 2009-01-12
```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda6 
                       and looks at sector 300669754 of the same hard drive 
                       for the stage2 file and on partition #6 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa325a97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  83  Linux
/dev/sda2   *    20467712   166793215    73162752    6  FAT16
/dev/sda3       166793216   280709119    56957952   83  Linux
/dev/sda4       280719809   321669494    20474843    f  W95 Ext'd (LBA)
/dev/sda5       280719810   282663674      971932+  82  Linux swap / Solaris
/dev/sda6       282663738   321669494    19502878+  83  Linux

sfdisk -V /dev/sda:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 2 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a293b3a1-fe32-4f04-9d4c-258a52db2be8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="5E002008001FE635" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="051a02bd-d608-4291-b09c-c58ff37ae656" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="79b94f5d-86bb-4770-839f-ea35a92f46ec" 
/dev/sda6: UUID="f9e12426-0382-45c3-aca8-77ca3aa83dfc" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda2 on /media/ACER type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aeronotix/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aeronotix)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=aeronotix)

================================== sda2/Boot: ==================================

total 988
drwxrwxrwx 1 root root   4096 2007-09-14 03:54 .
drwxrwxrwx 1 root root  28672 2009-01-12 22:10 ..
-rwxrwxrwx 1 root root 262144 2009-01-12 22:16 BCD
-rwxrwxrwx 1 root root 262144 2009-01-12 22:14 BCD.LOG
-rwxrwxrwx 1 root root  65536 2007-09-14 03:54 bootstat.dat
drwxrwxrwx 1 root root      0 2007-09-14 03:54 cs-CZ
drwxrwxrwx 1 root root      0 2007-09-14 03:54 da-DK
drwxrwxrwx 1 root root      0 2007-09-14 03:54 de-DE
drwxrwxrwx 1 root root      0 2007-09-14 03:54 el-GR
drwxrwxrwx 1 root root      0 2007-09-14 03:54 en-US
drwxrwxrwx 1 root root      0 2007-09-14 03:54 es-ES
drwxrwxrwx 1 root root      0 2007-09-14 03:54 fi-FI
drwxrwxrwx 1 root root      0 2007-09-14 03:54 Fonts
drwxrwxrwx 1 root root      0 2007-09-14 03:54 fr-FR
drwxrwxrwx 1 root root      0 2007-09-14 03:54 hu-HU
drwxrwxrwx 1 root root      0 2007-09-14 03:54 it-IT
drwxrwxrwx 1 root root      0 2007-09-14 03:54 ja-JP
drwxrwxrwx 1 root root      0 2007-09-14 03:54 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 09:51 memtest.exe
drwxrwxrwx 1 root root      0 2007-09-14 03:54 nb-NO
drwxrwxrwx 1 root root      0 2007-09-14 03:54 nl-NL
drwxrwxrwx 1 root root      0 2007-09-14 03:54 pl-PL
drwxrwxrwx 1 root root      0 2007-09-14 03:54 pt-BR
drwxrwxrwx 1 root root      0 2007-09-14 03:54 pt-PT
drwxrwxrwx 1 root root      0 2007-09-14 03:54 ru-RU
drwxrwxrwx 1 root root      0 2007-09-14 03:54 sv-SE
drwxrwxrwx 1 root root      0 2007-09-14 03:54 tr-TR
drwxrwxrwx 1 root root      0 2007-09-14 03:54 zh-CN
drwxrwxrwx 1 root root      0 2007-09-14 03:54 zh-HK
drwxrwxrwx 1 root root      0 2007-09-14 03:54 zh-TW

=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout		60

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
splashimage (hd0,5)/boot/grub/splashimages/splash.xpm.gz

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
# kopt=root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc             proc         defaults                     0  0  
# Entry for /dev/sda6 :
UUID=f9e12426-0382-45c3-aca8-77ca3aa83dfc  /                 ext3         relatime,errors=remount-ro   0  1  
# Entry for /dev/sda5 :
UUID=79b94f5d-86bb-4770-839f-ea35a92f46ec  none              swap         sw                           0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/sda2                                  /media/ACER       ntfs-3g      defaults,locale=en_GB.UTF-8  0  0  
/dev/sda1                                  /media/PQSERVICE  ntfs-3g      defaults,locale=en_GB.UTF-8  0  0  

================================== sda6/boot: ==================================

total 72308
drwxr-xr-x  3 root root    4096 2009-01-12 23:44 .
drwxr-xr-x 21 root root    4096 2009-01-08 23:10 ..
-rw-r--r--  1 root root  422667 2008-08-21 05:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 04:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 22:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80049 2008-08-21 05:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 04:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 22:13 config-2.6.24-23-generic
drwxr-xr-x  3 root root    4096 2009-01-08 23:10 grub
-rw-r--r--  1 root root 7499056 2008-10-24 11:47 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7890338 2008-10-24 02:24 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7497639 2008-11-13 15:49 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7500889 2008-11-06 00:25 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7498450 2008-12-28 00:29 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7497603 2008-11-29 00:49 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7498550 2009-01-12 23:44 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7498604 2009-01-08 23:11 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 11:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 05:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 04:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 22:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1921464 2008-08-21 05:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 04:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 22:13 vmlinuz-2.6.24-23-generic

=============================== sda6/boot/grub: ===============================

total 284
drwxr-xr-x 3 root root   4096 2009-01-08 23:10 .
drwxr-xr-x 3 root root   4096 2009-01-12 23:44 ..
-rw-r--r-- 1 root root    197 2008-10-24 02:24 default
-rw-r--r-- 1 root root     15 2008-10-24 02:24 device.map
-rw-r--r-- 1 root root   8056 2008-10-24 02:24 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-24 02:24 fat_stage1_5
-rw-r--r-- 1 root root  64599 2008-10-27 12:43 images
-rw-r--r-- 1 root root     16 2008-10-24 02:24 installed-version
-rw-r--r-- 1 root root   8608 2008-10-24 02:24 jfs_stage1_5
-rw-r--r-- 1 root root   6117 2009-01-08 23:10 menu.lst
-rw-r--r-- 1 root root   5685 2009-01-08 23:10 menu.lst~
-rw-r--r-- 1 root root   7324 2008-10-24 02:24 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-24 02:24 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-27 12:44 splashimages
-rw-r--r-- 1 root root    512 2008-10-24 02:24 stage1
-rw-r--r-- 1 root root 108356 2008-10-24 02:24 stage2
-rw-r--r-- 1 root root   9276 2008-10-24 02:24 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

Unsure if you'd want that but put it up just in case.

I was also thinking if I put the Windows MBR in then did the GrUB fix with the LiveCD do you think that might make it actually do it?

---

### Post by aeronotix on 2009-01-14
If anyone wants to know I have sorted the problem, I ended up restoring the windows mbr and then restored the GrUB bootloader. This has sorted my problem.

---

