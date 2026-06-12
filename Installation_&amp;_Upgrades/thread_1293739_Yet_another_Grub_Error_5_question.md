---
title: "Yet another Grub Error 5 question"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2009-10-17
Hi.

I've read through many grub error 5 posts and I'm still not able to solve my problem.

Here's the important part of my menu.lst file:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		dcdf8112-9263-485f-ba9a-713c4726abc1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dcdf8112-9263-485f-ba9a-713c4726abc1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dcdf8112-9263-485f-ba9a-713c4726abc1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dcdf8112-9263-485f-ba9a-713c4726abc1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dcdf8112-9263-485f-ba9a-713c4726abc1
kernel		/boot/memtest86+.bin
quiet


and here's the output of fdisk -l

```
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003b2cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        8666    69609613+  83  Linux
/dev/sdc2            8667        9039     2996122+   5  Extended
/dev/sdc5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

```


and here's the output of cat device.map

```
ubuntu@ubuntu:/$ cat /media/disk/boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

```

Hopefully that's enough diagnostic information that someone can help me.

What's got me stumped is the fact that there's no (hd0,0) line in my menu.lst file.

Any help would be appreciated.

Thank you!!

ADD:  here's the results of the boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sde3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003b2cc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   139,219,289   139,219,227  83 Linux
/dev/sdc2         139,219,290   145,211,534     5,992,245   5 Extended
/dev/sdc5         139,219,353   145,211,534     5,992,182  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sde1             132,039       133,005           967  c7 Syrinx
/dev/sde3       2,147,615,687 2,147,616,653           967  c7 Syrinx

/dev/sde3 ends after the last sector of /dev/sde

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda: UUID="d8efdacb-87c1-26e8-68cf-5e3251379179" TYPE="mdraid" 
/dev/sdb: UUID="5b0bacdc-051a-8964-68cf-5e3251379179" TYPE="mdraid" 
/dev/sdc1: UUID="8660bb72-5a14-4f56-b31d-5900d8820e44" TYPE="ext3" 
/dev/sdc5: UUID="0643fdd0-5490-4a98-b42f-8c45c8c59ecf" TYPE="swap" 
/dev/sdd: UUID="d8efdacb-87c1-26e8-68cf-5e3251379179" TYPE="mdraid" 
/dev/sde: UUID="5b0bacdc-051a-8964-68cf-5e3251379179" TYPE="mdraid" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8660bb72-5a14-4f56-b31d-5900d8820e44 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8660bb72-5a14-4f56-b31d-5900d8820e44

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8660bb72-5a14-4f56-b31d-5900d8820e44
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8660bb72-5a14-4f56-b31d-5900d8820e44 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8660bb72-5a14-4f56-b31d-5900d8820e44
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8660bb72-5a14-4f56-b31d-5900d8820e44 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8660bb72-5a14-4f56-b31d-5900d8820e44
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=8660bb72-5a14-4f56-b31d-5900d8820e44 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0643fdd0-5490-4a98-b42f-8c45c8c59ecf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   3.1GB: boot/grub/menu.lst
   3.1GB: boot/grub/stage2
   3.2GB: boot/initrd.img-2.6.28-11-generic
   3.1GB: boot/vmlinuz-2.6.28-11-generic
   3.2GB: initrd.img
   3.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde1


Unknown BootLoader  on sde3



=============================== StdErr Messages: ===============================

hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde3: No such file or directory
hexdump: /dev/sde3: No such file or directory

```

---

### Post by madhartigan on 2009-10-17
bump

---

### Post by oldfred on 2009-10-17
Do you have a bunch of new drives or are these not standard sata drives i.e. raid or someother special config?

You have no partitions on most of your drives, only your current third drive. If you set your third drive to first in BIOS will it boot? You have grub in both first & third drives, but even your first shows no partitions.
Since you are using UUID's grub on third drive if set to first should boot.

---

### Post by madhartigan on 2009-10-17
Thank you for your reply!!

Yes sda, sdb, sdd and sde are two RAID 1 volumes.

Not sure how it fixed it, but Super Grub Disk did the trick for me.

I just put the disk in booted the PC and selected the MBR=>Grub (Automatic) option from the Super Grub Disk menu and the next reboot worked.



LINK: [Super Grub Disk](www.supergrubdisk.org)



Thanks again for your reply.

---

