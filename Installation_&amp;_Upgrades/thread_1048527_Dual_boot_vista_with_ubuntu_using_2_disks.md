---
title: "Dual boot vista with ubuntu using 2 disks"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by milidoni on 2009-01-23
On my desktop I have two hard disks. 1st disk runs Vista, second Ubuntu desktop 8.10. I am trying to set up dual boot but with no luck. The only way to boot ubuntu is by changing the boot disk order from BIOS.
When I installed ubuntu for the first time I let it update it the mbr of the 1st hard drive and then I could not boot vista anymore. Anyway I restored the mbr so I am able to boot vista, but I need a more convenient way to boot ubuntu as well. The results below are useful in order to understand how my system is setup : 

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block. BootPart 
                       in the file /NST/nst_grub.mbr is trying to chain load 
                       sector #63 on boot drive #2
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot /NST

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst /etc/fstab /boot 
                       /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ef33cb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   413698047   206848000    7  HPFS/NTFS
/dev/sda2       413698048   976764927   281533440    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f817c78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   953023994   476511966   83  Linux
/dev/sdb2       953023995   976768064    11872035    5  Extended
/dev/sdb5       953024058   976768064    11872003+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="42689F0A689EFBBB" LABEL="C_Vista" TYPE="ntfs" 
/dev/sda2: UUID="324ADBAB4ADB69DD" LABEL="D_DATA" TYPE="ntfs" 
/dev/sdb1: UUID="00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="c12ea237-c481-49d6-9044-29066ed208f7" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda2 on /media/D_DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================== sda1/Boot: ==================================

total 532
drwxrwxrwx 1 root root   4096 2009-01-12 02:06 .
drwxrwxrwx 1 root root   8192 2009-01-22 20:20 ..
-rwxrwxrwx 1 root root  28672 2009-01-22 20:50 BCD
-rwxrwxrwx 1 root root  25600 2009-01-22 20:44 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-12 02:06 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-12 02:06 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-12 02:06 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-12 02:06 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-12 02:06 da-DK
drwxrwxrwx 1 root root      0 2009-01-12 02:06 de-DE
drwxrwxrwx 1 root root      0 2009-01-12 02:06 el-GR
drwxrwxrwx 1 root root      0 2009-01-12 02:06 en-US
drwxrwxrwx 1 root root      0 2009-01-12 02:06 es-ES
drwxrwxrwx 1 root root      0 2009-01-12 02:06 fi-FI
drwxrwxrwx 1 root root      0 2009-01-12 02:06 Fonts
drwxrwxrwx 1 root root      0 2009-01-12 02:06 fr-FR
drwxrwxrwx 1 root root      0 2009-01-12 02:06 hu-HU
drwxrwxrwx 1 root root      0 2009-01-12 02:06 it-IT
drwxrwxrwx 1 root root      0 2009-01-12 02:06 ja-JP
drwxrwxrwx 1 root root      0 2009-01-12 02:06 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-21 04:24 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-12 02:06 nb-NO
drwxrwxrwx 1 root root      0 2009-01-12 02:06 nl-NL
drwxrwxrwx 1 root root      0 2009-01-12 02:06 pl-PL
drwxrwxrwx 1 root root      0 2009-01-12 02:06 pt-BR
drwxrwxrwx 1 root root      0 2009-01-12 02:06 pt-PT
drwxrwxrwx 1 root root      0 2009-01-12 02:06 ru-RU
drwxrwxrwx 1 root root      0 2009-01-12 02:06 sv-SE
drwxrwxrwx 1 root root      0 2009-01-12 02:06 tr-TR
drwxrwxrwx 1 root root      0 2009-01-12 02:06 zh-CN
drwxrwxrwx 1 root root      0 2009-01-12 02:06 zh-HK
drwxrwxrwx 1 root root      0 2009-01-12 02:06 zh-TW

================================== sda1/NST: ==================================

total 9
drwxrwxrwx 1 root root    0 2009-01-22 20:43 .
drwxrwxrwx 1 root root 8192 2009-01-22 20:20 ..
-rwxrwxrwx 1 root root  512 2009-01-12 11:15 nst_grub.mbr

=========================== sdb1/boot/grub/menu.lst: ===========================

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
color cyan/blue white/blue

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
# kopt=root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d

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
# defoptions=quiet splash rootdelay=120

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
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro quiet splash rootdelay=120
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
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


================================ sdb1/menu.lst: ================================

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=00f4a0b4-9d06-4d6c-9f0d-d7abbfbd137d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=c12ea237-c481-49d6-9044-29066ed208f7 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 25540
drwxr-xr-x  3 root root    4096 2008-12-21 21:29 .
drwxr-xr-x 21 root root    4096 2008-11-29 20:30 ..
-rw-r--r--  1 root root  503560 2008-11-04 22:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-21 01:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 22:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-21 01:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-19 20:21 grub
-rw-r--r--  1 root root 8675718 2008-11-29 14:58 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8677817 2008-12-21 21:29 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 23:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 22:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-21 01:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 22:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-21 01:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 22:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-21 01:30 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-19 20:21 .
drwxr-xr-x 3 root root   4096 2008-12-21 21:29 ..
-rw-r--r-- 1 root root    197 2008-11-29 14:25 default
-rw-r--r-- 1 root root     30 2008-11-29 14:25 device.map
-rw-r--r-- 1 root root   8108 2008-11-29 14:25 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-29 14:25 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-29 14:25 installed-version
-rw-r--r-- 1 root root   8712 2008-11-29 14:25 jfs_stage1_5
-rw-r--r-- 1 root root   5116 2009-01-19 20:21 menu.lst
-rw-r--r-- 1 root root   5103 2009-01-19 20:21 menu.lst~
-rw-r--r-- 1 root root   5090 2008-11-29 17:53 menu.lst_original
-rw-r--r-- 1 root root   7352 2008-11-29 14:25 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-29 14:25 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-29 14:25 stage1
-rw-r--r-- 1 root root 121460 2008-11-29 14:25 stage2
-rw-r--r-- 1 root root   9556 2008-11-29 14:25 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
  
```

Any help would be appreciated. 
Stelios

---

### Post by cdtech on 2009-01-23
I run a dual drive setup using my primary as Ubuntu and secondary as my Vista. I started out with my primary (default) Vista and wanted to install Ubuntu but wanted to keep them both as segregated as possible. I removed the primary drive (Vista) and installed my new drive into bay 1 then installed Ubuntu, installing the MBR onto that drive alone.

Afterwards I reinstalled my Vista drive into bay 2, booted into the Ubuntu OS (primary drive) opened a terminal and modified my /boot/grub/menu.lst to include the Vista OS.
```
title		Windows Vista/Longhorn (loader)
root		(**hd1**,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by milidoni on 2009-01-23
Thanks for the answer.
I would prefer though to fix this problem "softly", just by setting up correctly the entries in the grub menu. How would you suggest to modify my menu.lst ? 
In your post you refer to hd1 & hd0. Once my son leaves the PC :-) (on a laptop now), I will try your suggestion using sdb & sda instead (is that right?) to see what will happen. Do you have any experience in using neo easybcd ?

Stelios

---

