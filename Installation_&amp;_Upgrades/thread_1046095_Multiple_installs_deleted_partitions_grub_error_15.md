---
title: "Multiple installs deleted partitions grub error 15"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by sawjam on 2009-01-21
Hi 

Background:

Windows XP PC 2 HD

undertook adventure into linux, installed multiple distro, looking at whats what, decided liked Ubuntu, spent long time getting DVB-S equipment to work, broke a few things! ended up with an install that works well.

Proceded to add another HD, intention to move ubuntu 8.10 to this drive, different discussion!

After deleting redundant partitions, not used, or with broken installs, grub has stopped work.

see output below of various info.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa555a555

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9f3b9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   204796619   102398278+   7  HPFS/NTFS
/dev/sdb2       282904650   625137344   171116347+   5  Extended
/dev/sdb5       621233550   625137344     1951897+  82  Linux swap / Solaris
/dev/sdb6       562612428   582147404     9767488+  83  Linux
/dev/sdb7       282920778   312223274    14651248+  83  Linux
/dev/sdb8       509871033   562612364    26370666   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ac231c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    29302559    14651248+  83  Linux
/dev/sdc2        29302560    58605119    14651280    5  Extended
/dev/sdc5        29302623    58605119    14651248+  83  Linux

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2AC0DE0DC0DDDEDF" TYPE="ntfs" 
/dev/sdb1: UUID="4C94ED0F94ECFC78" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="8425579c-035a-4226-8f4f-d68c2e817038" 
/dev/sdb6: UUID="801eb555-9295-4c88-a2dc-a1186c8d36f4" TYPE="ext3" 
/dev/sdb7: UUID="dcca9370-02b0-4060-8f6a-19f6916cd186" TYPE="ext3" 
/dev/sdb8: UUID="b4d2de99-54f6-43e0-a2ad-4930db016962" TYPE="ext3" 
/dev/sdc1: UUID="c7b2775a-9843-464a-8d86-cc3e50c2da5b" TYPE="ext3" 
/dev/sdc5: UUID="8f26e4fb-4b86-4ce7-b9c9-dcec898ecde1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb7 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb8 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb6 on /media/disk-3 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/disk-5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


=========================== sdb6/boot/grub/menu.lst: ===========================

default 0
timeout 10

title Windows XP Media Center Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb6)
root (hd1,5)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=773c65b6-4e7d-4e9a-a0b7-d8586603e533 ro single
initrd /boot/initrd.img-2.6.27-7-generic
savedefault

title Ubuntu 8.10, memtest86+ (on /dev/sdb6)
root (hd1,5)
kernel /boot/memtest86+.bin
savedefault


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb8 :
UUID=801eb555-9295-4c88-a2dc-a1186c8d36f4	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb10 :
UUID=b4d2de99-54f6-43e0-a2ad-4930db016962	/home	ext3	relatime	0	2
#Entry for /dev/sdb5 :
UUID=8425579c-035a-4226-8f4f-d68c2e817038	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



================================== sdb6/boot: ==================================

total 60048
drwxr-xr-x  3 root root    4096 2009-01-15 03:35 .
drwxr-xr-x 20 root root    4096 2009-01-15 03:34 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85837 2008-08-21 04:58 config-2.6.24-19-rt
-rw-r--r--  1 root root   86047 2008-11-27 22:25 config-2.6.24-23-rt
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-21 09:30 grub
-rw-r--r--  1 root root 7771072 2009-01-13 08:57 initrd.img-2.6.24-19-rt
-rw-r--r--  1 root root 7771895 2009-01-14 07:27 initrd.img-2.6.24-19-rt.bak
-rw-r--r--  1 root root 7774753 2009-01-13 08:57 initrd.img-2.6.24-23-rt
-rw-r--r--  1 root root 7775023 2009-01-13 08:56 initrd.img-2.6.24-23-rt.bak
-rw-r--r--  1 root root 8183469 2009-01-15 03:34 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8183271 2009-01-15 03:35 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root  928302 2008-08-21 04:58 System.map-2.6.24-19-rt
-rw-r--r--  1 root root  930168 2008-11-27 22:25 System.map-2.6.24-23-rt
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1960312 2008-08-21 04:58 vmlinuz-2.6.24-19-rt
-rw-r--r--  1 root root 1972504 2008-11-27 22:25 vmlinuz-2.6.24-23-rt
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sdb6/boot/grub: ===============================

total 236
drwxr-xr-x 2 root root   4096 2009-01-21 09:30 .
drwxr-xr-x 3 root root   4096 2009-01-15 03:35 ..
-rw-r--r-- 1 root root    197 2009-01-15 03:13 default
-rw-r--r-- 1 root root     30 2009-01-14 07:27 device.map
-rw-r--r-- 1 root root   8108 2009-01-15 03:13 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-15 03:13 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-15 03:13 installed-version
-rw-r--r-- 1 root root   8712 2009-01-15 03:13 jfs_stage1_5
-rw-r--r-- 1 root root    447 2009-01-21 09:38 menu.lst
-rw-r--r-- 1 root root   7755 2009-01-21 07:20 menu.lst~
-rw-r--r-- 1 root root   7635 2009-01-21 09:23 menu.lst~_original
-rw-r--r-- 1 root root   7755 2009-01-21 09:17 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-15 03:13 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-15 03:13 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-15 03:13 stage1
-rw-r--r-- 1 root root 121460 2009-01-15 03:13 stage2
-rw-r--r-- 1 root root   9556 2009-01-15 03:13 xfs_stage1_5

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7b2775a-9843-464a-8d86-cc3e50c2da5b

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
uuid		c7b2775a-9843-464a-8d86-cc3e50c2da5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c7b2775a-9843-464a-8d86-cc3e50c2da5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c7b2775a-9843-464a-8d86-cc3e50c2da5b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-19-rt root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-23-rt root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8f26e4fb-4b86-4ce7-b9c9-dcec898ecde1 /home           ext3    relatime        0       2
# /dev/sdc5
UUID=8425579c-035a-4226-8f4f-d68c2e817038 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 12404
drwxr-xr-x  3 root root    4096 2009-01-21 08:33 .
drwxr-xr-x 20 root root    4096 2009-01-21 08:33 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-21 08:33 grub
-rw-r--r--  1 root root 8639157 2009-01-21 08:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-rw-rw-  1 root root 2244272 2009-01-21 08:31 vmlinuz-2.6.27-7-generic

=============================== sdc1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-21 08:33 .
drwxr-xr-x 3 root root   4096 2009-01-21 08:33 ..
-rw-r--r-- 1 root root    197 2009-01-21 08:33 default
-rw-r--r-- 1 root root     45 2009-01-21 08:33 device.map
-rw-r--r-- 1 root root   8108 2009-01-21 08:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-21 08:33 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-21 08:33 installed-version
-rw-r--r-- 1 root root   8712 2009-01-21 08:33 jfs_stage1_5
-rw-r--r-- 1 root root   5753 2009-01-21 08:33 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-21 08:33 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-21 08:33 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-21 08:33 stage1
-rw-r--r-- 1 root root 121460 2009-01-21 08:33 stage2
-rw-r--r-- 1 root root   9556 2009-01-21 08:33 xfs_stage1_5

=============================== StdErr Messages: ===============================

sed: can't read sdb7/etc/issue: No such file or directory
```

tried several options to get grub working again, believe I just making things worst, been using live CD to mount and edit menu.lst

tried using live CD to install another distro on new HD, this previously worked when I broke grub last time, but not working now.

I'm very green and propably been a bit trigger happy with code, anyone provide some light into my dark cave?

---

### Post by Pumalite on 2009-01-21
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by caljohnsmith on 2009-01-21
Can you change your BIOS to boot either the sdb or sdc drive instead of the sda Windows drive? If you can boot your sdc drive for instance, it looks like everything is configured correctly for you to boot into your sdc1 8.10 Ubuntu install. Getting your sdb drive booting will take a little tweaking, so how about doing:
```
sudo sfdisk -A1 /dev/sdb
```
Then see if when you boot the sdb drive, and you should at least get the Grub menu. You won't actually be able to boot into Ubuntu on the sdb drive the way your menu.lst is currently configured; but getting the Grub menu is 90% of the battle, so see if you can get that far first. Let me know how it goes, and we can work from there if you want.

---

### Post by sawjam on 2009-01-21
Ok I can see some light from my cave, (hope it's not headlights!)

Changed boot sequence boot sdc: get grub menu can start installation of 8.10 on Sbc (Clean install not actual version I would like to recover) grub List for xp gives error NTLDR missing
list for 8.10 instalation on sdb6 error 21

Changed boot sequence sdb: get grub menu same issue 8.10 install on sdb6 error 21 xp NTLDR missing. (no list for 8.10 install on sbc)

(The 8.10 install on sdb is the one I've spent hours updating and would like to recover)

Havent tried: ```
sudo sfdisk -A1 /dev/sdb1
``` yet It stated I needed to force this command to use, this is the drive with my xp install too, could I lose any data?

Also looking at the [HTML]http://users.bigpond.net.au/hermanzone/p15.htm#15/HTML]

link too.

How can I be sure which grub menu/list i'm editing with so many versions on different drives?

---

### Post by caljohnsmith on 2009-01-21
My mistake, please see my previous post for the correct command (should use sdb instead of sdb1). Glad to hear that you get the Grub menu on start up when you boot either the sdb drive or the sdc drive, so to correct the menu.lst for each of them, how about doing:
```
sudo mkdir /mnt/sdb6 /mnt/sdc1
sudo mount /dev/sdb6 /mnt/sdb6
sudo mount /dev/sdc1 /mnt/sdc1
gksudo gedit /mnt/sdb6/boot/grub/menu.lst &
```
And then change the two Ubuntu entries to use (hd0,5) instead of (hd1,5), and also change your Windows entry to two entries:
```
title Windows XP Media Center Edition (hd1)
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

title Windows XP Media Center Edition (hd2)
root (hd2,0)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb6)
root [COLOR="Blue"](hd0,5)[/COLOR]
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=773c65b6-4e7d-4e9a-a0b7-d8586603e533 ro single
initrd /boot/initrd.img-2.6.27-7-generic
savedefault

title Ubuntu 8.10, memtest86+ (on /dev/sdb6)
root [COLOR="Blue"](hd0,5)[/COLOR]
kernel /boot/memtest86+.bin
savedefault
```
Next open your sdc1 menu.lst:
```
gksudo gedit /mnt/sdc1/boot/grub/menu.lst &
```
And change the Windows entry to:
```
title		Windows XP Media Center Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```
Also, to boot your sdb6 install from the sdc drive, how about trying:
```
title Ubuntu 8.10 on sdb6
root (hd1,5)
map  (hd1) (hd0)
map  (hd0) (hd1)
configfile /boot/grub/menu.lst
```
And lastly, since you can boot either the sdb or sdc drives on start up, I would recommend restoring a Windows MBR (Master Boot Record) to your sda drive since sda has your Windows install. That way if you boot the sda drive, you should be able to boot straight into Windows. To do that try:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then reboot, try booting each of your drives, and let me know exactly what happens. We can go from there.

---

### Post by sawjam on 2009-01-21
**[COLOR="Lime"]Thank you so much for your help, I'm out of the cave and admiring the view.[/COLOR]**

Had a few issues getting my head around all the drive name's i.e. sda-sdc issues because I'd changed the boot order of the hard drives so all the names changed!, but once around that started to go well. 

Slight typo here:

[QUOTE=
Next open your sdc1 menu.lst:
```
gksudo gedit /mnt/[COLOR="Blue"]boot/grub/[/COLOR]sdc1/menu.lst &
```
[/QUOTE]

So results:

Boot from drive ch0 - straight to XP no issues
Boot from drive ch1 - grub menu Ok

1 xp OK
2 xp invalid or unsuported executable format?
3 8.10 (recovery) avoids shell goes to some prompt I can't remember started with <i....> I think
4 8.10 memtest OK

Boot from drive ch4 - grub menu Ok

1 8.10 (Mythbuntu) OK
2 XP OK
3 8.10 on ch1 goes to grub menu above.


So I then edited the menu.lst with an additional line for my working 8.10 (which I found the info in an old menu.lst_original file in the grub boot directory!)

Output of Boot info summary (see blue added code and if you feel like helping some more see red, whats wrong with the 2nd XP choice? and what's the last line?)

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa555a555

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9f3b9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdb2       282904650   625137344   171116347+   5  Extended
/dev/sdb5       621233550   625137344     1951897+  82  Linux swap / Solaris
/dev/sdb6       562612428   582147404     9767488+  83  Linux
/dev/sdb7       282920778   312223274    14651248+  83  Linux
/dev/sdb8       509871033   562612364    26370666   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ac231c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    29302559    14651248+  83  Linux
/dev/sdc2        29302560    58605119    14651280    5  Extended
/dev/sdc5        29302623    58605119    14651248+  83  Linux

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2AC0DE0DC0DDDEDF" TYPE="ntfs" 
/dev/sdb1: UUID="4C94ED0F94ECFC78" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="8425579c-035a-4226-8f4f-d68c2e817038" 
/dev/sdb6: UUID="801eb555-9295-4c88-a2dc-a1186c8d36f4" TYPE="ext3" 
/dev/sdb7: UUID="dcca9370-02b0-4060-8f6a-19f6916cd186" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="b4d2de99-54f6-43e0-a2ad-4930db016962" TYPE="ext3" 
/dev/sdc1: UUID="c7b2775a-9843-464a-8d86-cc3e50c2da5b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="8f26e4fb-4b86-4ce7-b9c9-dcec898ecde1" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb8 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jmze/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jmze)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


=========================== sdb6/boot/grub/menu.lst: ===========================

default 0
timeout 10

title Windows XP Media Center Edition (hd1)
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
#savedefault
#makeactive

[COLOR="Red"]title Windows XP Media Center Edition (hd2)
root (hd2,0)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1[/COLOR]

[COLOR="Blue"]title Ubuntu 8.10, kernel 2.6.27-9 generic (hope)
root (hd0,5)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=801eb555-9295-4c88-a2dc-a1186c8d36f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
savedefault[/COLOR]

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=773c65b6-4e7d-4e9a-a0b7-d8586603e533 ro single
initrd /boot/initrd.img-2.6.27-7-generic
savedefault

title Ubuntu 8.10, memtest86+ (on /dev/sdb6)
root (hd0,5)
kernel /boot/memtest86+.bin
savedefault


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb8 :
UUID=801eb555-9295-4c88-a2dc-a1186c8d36f4	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb10 :
UUID=b4d2de99-54f6-43e0-a2ad-4930db016962	/home	ext3	relatime	0	2
#Entry for /dev/sdb5 :
UUID=8425579c-035a-4226-8f4f-d68c2e817038	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



================================== sdb6/boot: ==================================

total 60048
drwxr-xr-x  3 root root    4096 2009-01-15 16:35 .
drwxr-xr-x 20 root root    4096 2009-01-15 16:34 ..
-rw-r--r--  1 root root  507665 2008-11-05 10:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-21 12:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85837 2008-08-21 16:58 config-2.6.24-19-rt
-rw-r--r--  1 root root   86047 2008-11-28 11:25 config-2.6.24-23-rt
-rw-r--r--  1 root root   91364 2008-11-05 10:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-21 12:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-22 15:09 grub
-rw-r--r--  1 root root 7771072 2009-01-13 21:57 initrd.img-2.6.24-19-rt
-rw-r--r--  1 root root 7771895 2009-01-14 20:27 initrd.img-2.6.24-19-rt.bak
-rw-r--r--  1 root root 7774753 2009-01-13 21:57 initrd.img-2.6.24-23-rt
-rw-r--r--  1 root root 7775023 2009-01-13 21:56 initrd.img-2.6.24-23-rt.bak
-rw-r--r--  1 root root 8183469 2009-01-15 16:34 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8183271 2009-01-15 16:35 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-12 08:11 memtest86+.bin
-rw-r--r--  1 root root  928302 2008-08-21 16:58 System.map-2.6.24-19-rt
-rw-r--r--  1 root root  930168 2008-11-28 11:25 System.map-2.6.24-23-rt
-rw-r--r--  1 root root 1029585 2008-11-05 10:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-21 12:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-05 10:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-21 12:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1960312 2008-08-21 16:58 vmlinuz-2.6.24-19-rt
-rw-r--r--  1 root root 1972504 2008-11-28 11:25 vmlinuz-2.6.24-23-rt
-rw-r--r--  1 root root 2244464 2008-11-05 10:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-21 12:46 vmlinuz-2.6.27-9-generic

=============================== sdb6/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-22 15:09 .
drwxr-xr-x 3 root root   4096 2009-01-15 16:35 ..
-rw-r--r-- 1 root root    197 2009-01-15 16:13 default
-rw-r--r-- 1 root root     30 2009-01-14 20:27 device.map
-rw-r--r-- 1 root root   8108 2009-01-15 16:13 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-15 16:13 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-15 16:13 installed-version
-rw-r--r-- 1 root root   8712 2009-01-15 16:13 jfs_stage1_5
-rw-r--r-- 1 root root    818 2009-01-22 15:09 menu.lst
-rw-r--r-- 1 root root    818 2009-01-22 15:08 menu.lst~
-rw-r--r-- 1 root root   7635 2009-01-21 22:23 menu.lst~_original
-rw-r--r-- 1 root root   7755 2009-01-21 22:17 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-15 16:13 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-15 16:13 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-15 16:13 stage1
-rw-r--r-- 1 root root 121460 2009-01-15 16:13 stage2
-rw-r--r-- 1 root root   9556 2009-01-15 16:13 xfs_stage1_5

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7b2775a-9843-464a-8d86-cc3e50c2da5b

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
uuid		c7b2775a-9843-464a-8d86-cc3e50c2da5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c7b2775a-9843-464a-8d86-cc3e50c2da5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c7b2775a-9843-464a-8d86-cc3e50c2da5b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


title		Ubuntu 8.10 on sdb6
root		(hd1,5)
map		(hd1) (hd0)
map		(hd0) (hd1)
configfile /boot/grub/menu.lst


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-19-rt root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-23-rt root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc6.
title		Ubuntu 8.10 (8.10) (on /dev/sdc6)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/sdc6 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c7b2775a-9843-464a-8d86-cc3e50c2da5b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8f26e4fb-4b86-4ce7-b9c9-dcec898ecde1 /home           ext3    relatime        0       2
# /dev/sdc5
UUID=8425579c-035a-4226-8f4f-d68c2e817038 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 12408
drwxr-xr-x  3 root root    4096 2009-01-22 14:20 .
drwxr-xr-x 20 root root    4096 2009-01-22 14:33 ..
-rw-r--r--  1 root root  507665 2008-10-24 21:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root     512 2009-01-22 14:20 boot.0810
-rw-r--r--  1 root root   91364 2008-10-24 21:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-22 14:18 grub
-rw-r--r--  1 root root 8639157 2009-01-21 21:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-12 08:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 21:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 21:31 vmcoreinfo-2.6.27-7-generic
-rw-rw-rw-  1 root root 2244272 2009-01-21 21:31 vmlinuz-2.6.27-7-generic

=============================== sdc1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-22 14:18 .
drwxr-xr-x 3 root root   4096 2009-01-22 14:20 ..
-rw-r--r-- 1 root root    197 2009-01-21 21:33 default
-rw-r--r-- 1 root root     45 2009-01-21 21:33 device.map
-rw-r--r-- 1 root root   8108 2009-01-21 21:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-21 21:33 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-21 21:33 installed-version
-rw-r--r-- 1 root root   8712 2009-01-21 21:33 jfs_stage1_5
-rw-r--r-- 1 root root   5861 2009-01-22 14:18 menu.lst
-rw-r--r-- 1 root root   5753 2009-01-22 14:12 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-21 21:33 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-21 21:33 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-21 21:33 stage1
-rw-r--r-- 1 root root 121460 2009-01-21 21:33 stage2
-rw-r--r-- 1 root root   9556 2009-01-21 21:33 xfs_stage1_5

=============================== StdErr Messages: ===============================

[COLOR="Red"]sed: can't read sdb7/etc/issue: No such file or directory[/COLOR]
```

---

### Post by caljohnsmith on 2009-01-21
I should have mentioned that once you found which XP entry worked, you can delete the other one; therefore you can get rid of the Windows XP (hd2) entry since the (hd1) entry worked. About your Ubuntu entries, it looks like you also need the correct the UUID of the recovery mode entry:
```
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=[COLOR="Blue"]801eb555-9295-4c88-a2dc-a1186c8d36f4[/COLOR] ro single
initrd /boot/initrd.img-2.6.27-7-generic
savedefault

```
But the blue Ubuntu entry that you added looks like it should work just fine, so let me know what happens when you boot it. :)

---

### Post by sawjam on 2009-01-21
Sweet!

A - OK

:D

---

