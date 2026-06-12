---
title: "install faillure... Raid1, dual boot - dead OS"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by cyberjean on 2009-03-20
Brand new computer.
2*250G hard disk
RAID1 installed... I believed it is a real one (though it could be a fake one, I have doubt about everything now!)
WinXP 64 pre-installed


Hello all,

I tried to install Ubuntu 8.10 (desktop-amd64), and it ruined my computer. I made the mistake to use first the desktop, before the alternate disk. Moreover, the installation failed a first time, and was kind of successful a second time.

If I boot my computer, right after the bios, I just see a black screen (no cursor, no grub, no windows, nothing!). I have even tried to put the Reinstallation CD (for windows, from Dell)... same black screen!

I can start with the live CD (at least!!), and I see that the installation was almost complete. Almost, as I can not see grub! (/boot/ contains:
-abi02.6.27-7-generic
-config-2.6.27-7-generic
-memtest86+.bin
-system,nao-2.6.27-7-generic
-vmcoreinfo-2.6.27-7-generic )





Now, the maybe good new is:
```
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 30394 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+      8       9-     72261   de  Dell Utility
/dev/sda2   *      9   15352   15344  123250680    7  HPFS/NTFS
/dev/sda3      15353   30393   15041  120816832+   5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      15353+  29776   14424- 115860748+  83  Linux
/dev/sda6      29777+  30393     617-   4956021   82  Linux swap / Solaris

Disk /dev/sdb: 30394 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+      8       9-     72261   de  Dell Utility
/dev/sdb2   *      9   15170   15162  121788765    7  HPFS/NTFS
/dev/sdb3      15171   30393   15223  122278747+   5  Extended
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5      15171+  29769   14599- 117266436   83  Linux
/dev/sdb6      29770+  30393     624-   5012248+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```


So, I see that my windows partition, and the dell partition are still there! Great! ... but but but, the partitions on the 2nd disk (raid1 = mirror of the 1st disk) are not the same size anymore, compared to the 1st disk!



After reading some posts here, I have burnt the alternate-amd64 installer... now it did recognized my raid, great, but at the time of "selecting" the partition, it gave me no choice and told me that the 250gb disk was already a linux only partition!... and I could not find a way to either see the other existing partitions or to use a smaller size... maybe I didn't went "far" enough, but the 1 000 warnings that the partitions and the content would be lost made me a tad reluctant.

So, anyways, I am now stuck with a brand new computer that won't load windows nor Ubuntu...  any advice anyone???? 

Thanks in advance!
PS: I am no linux expert but I have had some hands on FC6 and understand the concepts

---

### Post by cyberjean on 2009-03-20
Here are more info, from sudo bash ~/Desktop/boot_info_script*.sh

could it just be that grub is not properly installed???

thanks again!
Jean

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ecab17e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2    *        144,585   246,645,944   246,501,360   7 HPFS/NTFS
/dev/sda3         246,645,945   488,279,609   241,633,665   5 Extended
/dev/sda5         246,646,008   478,367,504   231,721,497  83 Linux
/dev/sda6         478,367,568   488,279,609     9,912,042  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ecab17e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       144,584       144,522  de Dell Utility
/dev/sdb2    *        144,585   243,722,114   243,577,530   7 HPFS/NTFS
/dev/sdb3         243,722,115   488,279,609   244,557,495   5 Extended
/dev/sdb5         243,722,178   478,255,049   234,532,872  83 Linux
/dev/sdb6         478,255,113   488,279,609    10,024,497  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 256 MB, 256901120 bytes
16 heads, 32 sectors/track, 980 cylinders, total 501760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d769c0f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32       501,759       501,728   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-030D" TYPE="vfat" 
/dev/sda2: UUID="58D03745D0372920" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="7a44416e-9fcf-41cf-9a9a-b76e3ec045f9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="0f39ca76-410a-48c8-989d-31bbb7e251f3" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-030D" TYPE="vfat" 
/dev/sdb2: UUID="58D03745D0372920" LABEL="OS" TYPE="ntfs" 
/dev/sdb5: UUID="1bd0cace-26cd-40d0-8338-e6de8cc04b16" TYPE="ext3" 
/dev/sdb6: UUID="5453b999-1993-401a-8fc1-79fe80b4126d" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="KINGSTON" UUID="C89E-660E" TYPE="vfat" 

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
/dev/sdb2 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7a44416e-9fcf-41cf-9a9a-b76e3ec045f9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a44416e-9fcf-41cf-9a9a-b76e3ec045f9

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
uuid		7a44416e-9fcf-41cf-9a9a-b76e3ec045f9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a44416e-9fcf-41cf-9a9a-b76e3ec045f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7a44416e-9fcf-41cf-9a9a-b76e3ec045f9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a44416e-9fcf-41cf-9a9a-b76e3ec045f9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7a44416e-9fcf-41cf-9a9a-b76e3ec045f9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Professional x64 Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows XP Professional x64 Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7a44416e-9fcf-41cf-9a9a-b76e3ec045f9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0f39ca76-410a-48c8-989d-31bbb7e251f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 210.5GB: boot/grub/menu.lst
 210.6GB: boot/grub/stage2
 210.7GB: boot/initrd.img-2.6.27-7-generic
 210.6GB: boot/vmlinuz-2.6.27-7-generic
 210.7GB: initrd.img
 210.6GB: vmlinuz

================================ sdb2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=1bd0cace-26cd-40d0-8338-e6de8cc04b16 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=5453b999-1993-401a-8fc1-79fe80b4126d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

```

---

### Post by cyberjean on 2009-03-22
Problem half solved... Ubuntu is installed, but windows still won't work... I will start a new thread.

For those in the same situation, I started with LiveCD, erased the linux partitions, re-install Ubuntu with the alternate CD, which did recognize my raid1 array! Great! It even told me that I have Windows and that it will be added to the OS boot choice. It didn't. I added it manually but other errors prevent me from starting windows.

---

