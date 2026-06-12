---
title: "[SOLVED] Yet another GRUB question"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by MadsRH on 2009-01-11
Hi :confused:
I was triple booting and everything was running just fine, until XP (I think it was XP) caused some kind of error. Now I boot directly into XP (and of course no one wants that!) without entering GRUB first.

When I try to "root (hd0,0)" in the terminal, I get a error 21: *Selected disk does not exist*


To help debug the problem I ran [this script]("http://ubuntuforums.org/member.php?u=530779") and heres the output:

Thanks in advance for taking the time to help out :P

```

============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 78 Heads and 14 sectors per Track. No errors 
                       found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /grldr /Boot

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb3: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
78 heads, 14 sectors/track, 286247 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7a0d7a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          14   312580631   156290309    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000077fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *    30716280   476230859   222757290    7  HPFS/NTFS
/dev/sdb2              63    30716279    15358108+  83  Linux
/dev/sdb3       476230860   488392064     6080602+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sdb:

partition 1: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D27C5E187C5DF825" TYPE="ntfs" 
/dev/sdb1: UUID="62E31A6863E901D8" TYPE="ntfs" 
/dev/sdb2: UUID="32742300-8e1f-4a09-9920-8aeef39c5916" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="cf0376fc-5859-41f8-9fb1-80a9a68d02d0" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-12-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-12-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================== sdb1/Boot: ==================================

total 548
drwxrwxrwx 1 root root   4096 2008-11-05 21:45 .
drwxrwxrwx 1 root root  28672 2009-01-11 10:06 ..
-rwxrwxrwx 1 root root  24576 2009-01-10 18:24 BCD
-rwxrwxrwx 1 root root  21504 2009-01-10 18:24 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-07-24 05:06 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-07-24 05:06 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-07-24 05:06 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-22 15:38 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-22 15:38 da-DK
drwxrwxrwx 1 root root      0 2008-12-22 15:38 de-DE
drwxrwxrwx 1 root root      0 2008-12-22 15:38 el-GR
drwxrwxrwx 1 root root      0 2008-12-22 15:38 en-US
drwxrwxrwx 1 root root      0 2008-12-22 15:38 es-ES
drwxrwxrwx 1 root root      0 2008-12-22 15:38 fi-FI
drwxrwxrwx 1 root root   4096 2008-11-05 21:45 Fonts
drwxrwxrwx 1 root root      0 2008-12-22 15:38 fr-FR
drwxrwxrwx 1 root root      0 2008-12-22 15:38 hu-HU
drwxrwxrwx 1 root root      0 2008-12-22 15:38 it-IT
drwxrwxrwx 1 root root      0 2008-12-22 15:38 ja-JP
drwxrwxrwx 1 root root      0 2008-12-22 15:38 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-22 15:38 nb-NO
drwxrwxrwx 1 root root      0 2008-12-22 15:38 nl-NL
drwxrwxrwx 1 root root      0 2008-12-22 15:38 pl-PL
drwxrwxrwx 1 root root      0 2008-12-22 15:38 pt-BR
drwxrwxrwx 1 root root      0 2008-12-22 15:38 pt-PT
drwxrwxrwx 1 root root      0 2008-12-22 15:38 ru-RU
drwxrwxrwx 1 root root      0 2008-12-22 15:38 sv-SE
drwxrwxrwx 1 root root      0 2008-12-22 15:38 tr-TR
drwxrwxrwx 1 root root      0 2008-12-22 15:38 zh-CN
drwxrwxrwx 1 root root      0 2008-12-22 15:38 zh-HK
drwxrwxrwx 1 root root      0 2008-12-22 15:38 zh-TW

=========================== sdb2/boot/grub/menu.lst: ===========================

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
timeout		7

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
# kopt=root=UUID=32742300-8e1f-4a09-9920-8aeef39c5916 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=32742300-8e1f-4a09-9920-8aeef39c5916 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=32742300-8e1f-4a09-9920-8aeef39c5916 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=32742300-8e1f-4a09-9920-8aeef39c5916 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=32742300-8e1f-4a09-9920-8aeef39c5916 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,1)
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=32742300-8e1f-4a09-9920-8aeef39c5916 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=cf0376fc-5859-41f8-9fb1-80a9a68d02d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb2/boot: ==================================

total 23652
drwxr-xr-x  3 root root    4096 2008-12-17 21:54 .
drwxr-xr-x 20 root root    4096 2008-11-28 08:58 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-22 09:17 grub
-rw-r--r--  1 root root 8123824 2008-11-27 21:51 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8125720 2008-12-17 21:54 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sdb2/boot/grub: ===============================

total 236
drwxr-xr-x 3 root root   4096 2008-12-22 09:17 .
drwxr-xr-x 3 root root   4096 2008-12-17 21:54 ..
-rw-r--r-- 1 root root    197 2008-10-09 21:38 default
-rw-r--r-- 1 root root     30 2008-10-09 21:38 device.map
-rw-r--r-- 1 root root   8108 2008-10-09 21:38 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-10-09 21:38 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-09 21:38 installed-version
-rw-r--r-- 1 root root   8712 2008-10-09 21:38 jfs_stage1_5
-rw-r--r-- 1 root root   5142 2008-12-22 09:17 menu.lst
-rw-r--r-- 1 root root   5142 2008-12-22 09:17 menu.lst~
-rw-r--r-- 1 root root   5996 2008-10-12 10:13 menu.lst.backup
-rw-r--r-- 1 root root   7352 2008-10-09 21:38 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-10-09 21:38 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-12 10:13 splashimages
-rw-r--r-- 1 root root    512 2008-10-09 21:38 stage1
-rw-r--r-- 1 root root 121500 2008-10-09 21:38 stage2
-rw-r--r-- 1 root root   9556 2008-10-09 21:38 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
hexdump: sdb1/AnotherWorldWP8NoPeopleVersion_by_night_fate.zip: No such file or directory
hexdump: sdb1/AnotherWorldWP8NoPeopleVersion_by_night_fate.zip: No such file or directory

```

---

### Post by Pumalite on 2009-01-11
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by MadsRH on 2009-01-11
Thanks, but not very useful though! :confused:
I know how to setup dualboot, but the problem is that it's not working. I still get a error 21: Selected disk does not exist

---

### Post by caljohnsmith on 2009-01-11
How about trying:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd0)
grub> quit
```
Let me know if that works OK, and if not, what problems you run into.

---

### Post by MadsRH on 2009-01-11
Thanks for the reply.
I still get the same error from **root (hd1,1)** and if I try **setup (hd0)** I get *error 12: Invalid device requested*
:confused:

---

### Post by caljohnsmith on 2009-01-11
Did you run the grub command with sudo? How about posting the output of all the following commands by copying/pasting everything in your terminal to the Ubuntu forum message box:
```
sudo fdisk -lu
sudo grub
grub> root (hd1,1)
grub> setup (hd0)
grub> quit
```

---

### Post by MadsRH on 2009-01-11
I think the **fdisk -lu **did it! :p
I'll just try rebooting

```
sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
78 heads, 14 sectors/track, 286247 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7a0d7a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          14   312580631   156290309    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000077fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *    30716280   476230859   222757290    7  HPFS/NTFS
/dev/sdb2              63    30716279    15358108+  83  Linux
/dev/sdb3       476230860   488392064     6080602+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by MadsRH on 2009-01-11
THANK YOU! It works! :p

I'm grateful for your help and fast reply - thanks ):P

---

### Post by caljohnsmith on 2009-01-11
Glad to hear that did the trick and you can boot Ubuntu OK now. Cheers and have fun with Windows and Ubuntu. :)

---

