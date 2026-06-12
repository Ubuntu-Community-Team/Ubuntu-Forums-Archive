---
title: "Partitioning problem: gparted doesn't see partitions"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by delucamarco on 2009-02-26
Hello,

After re-shuffling my partitions, my laptop boots and mounts them all properly - except I can't run gparted, as it logs the following and it doesn't show the partitions on my disk (actually it only shows the whole disk space as unallocated):

```

me@ike:~$ sudo gparted
======================
libparted : 1.7.1
======================
Cannot have overlapping partitions.

```

Being able to run gparted is not a big deal, but I understand there's something badly wrong with my disk's partition table and I'd like to fix it.
To doublecheck partition tables were ok, I tried and reboot from Windows' CD and it wouldn't even start the installation - it gets stuck on hardware probing or whatever it is it does before the attractive blue screen text interface.

Below, the output of fdisk and sfdisk:

```

me@ike:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2513f11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    79875242    39937590    5  Extended
/dev/sda2           16065     4000184     1992060   82  Linux swap / Solaris
/dev/sda3         4000185    19808144     7903980   83  Linux
/dev/sda4        19808145    73577699    26884777+  83  Linux
me@ike:~$ sudo sfdisk -d /dev/sda3
Warning: start=4000185 - this looks like a partition rather than
the entire disk. Using fdisk on it is probably meaningless.
[Use the --force option if you really want this]
me@ike:~$ sudo sfdisk --force -d /dev/sda3
# partition table of /dev/sda3
unit: sectors

/dev/sda3p1 : start=        0, size=        0, Id= 0
/dev/sda3p2 : start=        0, size=        0, Id= 0
/dev/sda3p3 : start=        0, size=        0, Id= 0
/dev/sda3p4 : start=        0, size=        0, Id= 0

```

Any help would be very much appreciated.

Thanks in advance,
Marco

---

### Post by caljohnsmith on 2009-02-26
It looks like the problem is primary partitions sda2, sda3, and sda4 are all inside of your sda1 extended partition; therefore they should be logical partitions, or the extended partition should be deleted. Do you know whether sda2, sda3, and sda4 should be primary partitions, or were they logical partitions before? If you are unsure, we can probably deduce it from the results of the "Boot Info Script". To run the Boot Info Script, first download it to your Ubuntu desktop (can be the Live CD if you want):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, and also post the output of:
```
sudo sfdisk -d /dev/sda
```
And lastly, what partition changes were you planning on making with gparted? That could influence what might be the best way to fix your partition table.

---

### Post by delucamarco on 2009-02-27
Firstly, thank you very much for replying.

Before the change, I had 3 contiguous primary partitions (sda1, sda2, sda3) and some free unallocated space at the end of the disk.
I wanted to install Windows on the free space but it wouldn't let me as it moaned the maximum number of partitions had been reached - fair enough.

To fix this problem, I thought my best options would be to wrap the three partitions in an extended partitions.
So I:
* shrank the first partition (sda1) in order to leave a little space before it to create the extended partition;
* created the extended partition, to start at block 63 and end a few megs after the last one;
* renamed the partitions so that the extended would be sda1 and the remaining sda2, sda3, sda4 respectively.

I ran the script, and here's the output you requested:

```

me@ike:~$ sudo ./boot_info_script27.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information...
Searching sda2 for information...
Searching sda3 for information...
Searching sda4 for information...
Finished. The results are in the file RESULTS.txt located in /home/mdeluca
me@ike:~$ cat RESULTS.txt 
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2513f11

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    79,875,242    79,875,180   5 Extended
Empty Partition
/dev/sda2              16,065     4,000,184     3,984,120  82 Linux swap / Solaris
/dev/sda3           4,000,185    19,808,144    15,807,960  83 Linux
/dev/sda4          19,808,145    73,577,699    53,769,555  83 Linux

/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: TYPE="swap" UUID="02b4322b-d396-4044-bda9-ec1c0b04b64d" 
/dev/sda3: UUID="b8584062-e1f7-4d33-80a1-ac82ff0c2c6a" TYPE="reiserfs" 
/dev/sda4: UUID="d4f331b4-353b-4de3-a863-5c63c9010580" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type reiserfs (rw,relatime,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda4 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
gvfs-fuse-daemon on /home/mdeluca/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mdeluca)


=========================== sda3/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b8584062-e1f7-4d33-80a1-ac82ff0c2c6a /               reiserfs notail,relatime 0       1
# /dev/sda4
UUID=d4f331b4-353b-4de3-a863-5c63c9010580 /home           ext3    relatime        0       2
# /dev/sda2
UUID=02b4322b-d396-4044-bda9-ec1c0b04b64d none            swap    sw              0       0
#UUID=05c56426-a7ca-4c02-b17b-d43b6611290a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/menu.lst
   2.4GB: boot/grub/stage2
   2.4GB: boot/initrd.img-2.6.24-19-generic
   2.4GB: boot/initrd.img-2.6.24-19-generic.bak
   3.2GB: boot/initrd.img-2.6.24-21-generic
   2.7GB: boot/initrd.img-2.6.24-21-generic.bak
   2.5GB: boot/initrd.img-2.6.24-22-generic
   3.3GB: boot/initrd.img-2.6.24-22-generic.bak
   2.5GB: boot/initrd.img-2.6.24-23-generic
   2.5GB: boot/initrd.img-2.6.24-23-generic.bak
   2.4GB: boot/vmlinuz-2.6.24-19-generic
   3.0GB: boot/vmlinuz-2.6.24-21-generic
   2.9GB: boot/vmlinuz-2.6.24-22-generic
   2.5GB: boot/vmlinuz-2.6.24-23-generic
   2.5GB: initrd.img
   2.5GB: initrd.img.old
   2.5GB: vmlinuz
   2.9GB: vmlinuz.old
me@ike:~$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 79875180, Id= 5
/dev/sda2 : start=    16065, size=  3984120, Id=82
/dev/sda3 : start=  4000185, size= 15807960, Id=83
/dev/sda4 : start= 19808145, size= 53769555, Id=83

```

Thanks again
Marco

---

### Post by caljohnsmith on 2009-02-27
OK, if you want to make sda2, sda3, and sda4 logical partitions, you will need to resize sda2 and sda3 just a little (63 sectors is all) so you make room for the EBRs (Extended Boot Records) that are associated with logical partitions; we can resize the sda2 swap partition when we convert sda2, sda3 and sda4 into logical paritions, but sda3 needs to be resized before doing that. So how about doing the following from a Live CD:
```

sudo umount /dev/sda3
sudo e2fsck -fv /dev/sda3
sudo resize2fs /dev/sda3 15807897s
sudo e2fsck -fv /dev/sda3

```
Please post the output of all the above commands.

---

### Post by delucamarco on 2009-02-28
I checked, resized and checked again sda3 as you suggested, except I replaced the ext2 commands with their reiserfs-equivalents as sda3's file system type is reiserfs (not ext2).

1) Check before resize:

```

ubuntu@ubuntu:/$ sudo reiserfsck /dev/sda3 --fix-fixable -y
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will check consistency of the filesystem on /dev/sda3
and will fix what can be fixed without --rebuild-tree
Will put log info to 'stdout'
###########
reiserfsck --fix-fixable started at Sat Feb 28 13:49:05 2009
###########
Replaying journal..
Reiserfs journal '/dev/sda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
	Leaves 10886
	Internal nodes 76
	Directories 25956
	Other files 228231
	Data block pointers 1469283 (84 of them are zero)
	Safe links 0
###########
reiserfsck finished at Sat Feb 28 13:49:42 2009
###########

```

2) Resize:

```

ubuntu@ubuntu:/$ sudo resize_reiserfs -s8093643264 /dev/sda3
resize_reiserfs 3.6.19 (2003 www.namesys.com)

ReiserFS report:
blocksize             4096
block count           1975987 (1975984)
free blocks           487555 (487552)
bitmap block count    61 (61)

Syncing..done


resize_reiserfs: Resizing finished successfully.

```

3) Check after resize:

```

ubuntu@ubuntu:/$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 79875180, Id= 5
/dev/sda2 : start=    16065, size=  3984120, Id=82
/dev/sda3 : start=  4000185, size= 15807960, Id=83
/dev/sda4 : start= 19808145, size= 53769555, Id=83

ubuntu@ubuntu:/$ sudo reiserfsck --fix-fixable /dev/sda3
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will check consistency of the filesystem on /dev/sda3
and will fix what can be fixed without --rebuild-tree
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --fix-fixable started at Sat Feb 28 14:18:15 2009
###########
Replaying journal..
Reiserfs journal '/dev/sda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished                  
Comparing bitmaps..finished
Checking Semantic tree:
finished                                                                       
No corruptions found
There are on the filesystem:
	Leaves 10886
	Internal nodes 76
	Directories 25956
	Other files 228231
	Data block pointers 1469283 (84 of them are zero)
	Safe links 0
###########
reiserfsck finished at Sat Feb 28 14:19:43 2009
###########

```

It seems to me that sda3 hasn't shrunk though?

---

### Post by caljohnsmith on 2009-02-28
.

---

### Post by delucamarco on 2009-02-28
?

---

### Post by caljohnsmith on 2009-03-01
.

---

### Post by jwsawyer on 2009-03-06
My PC starte having problems so I deleted all partitions and am trying to reinstall Ubunbtu 8.04-2.  It hangs up when trying to partition the hard drive.  It hangs at "Scanning disks ..."

---

