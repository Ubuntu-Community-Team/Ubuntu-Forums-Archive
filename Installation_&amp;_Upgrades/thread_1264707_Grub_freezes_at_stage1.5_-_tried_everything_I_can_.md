---
title: "Grub freezes at stage1.5 - tried everything I can think of..."
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by Raptor Ramjet on 2009-09-12
Hello,

I've just attempted to replace the single ATA hard drive in my mini-itx server with a new 1Tb sata drive.  So I copied all the files over to the new drive with "cp -ax" and have now removed the ATA drive.

However try as I might (I've been at this since 10:00 this morning - which is 8 hours) I simply cannot get Grub to get beyond "Loading Stage1.5".

To cut a very long story short I've been trying to install grub using a live CD in combination with the following commands (which I googled earlier):

```

# Make temp directory.
sudo mkdir /tmp/hd

# Mount "/" sata partition to temp directory.
sudo mount /dev/sda1 /tmp/hd

# Mount "proc" and "/dev" to temp directory (otherwise grub doesn't find stage1)
sudo mount -t proc none /tmp/hd/proc

sudo mount -o bind /dev /tmp/hd/dev

# Change root to temp directory.
sudo chroot /tmp/hd /bin/bash

# Enter grub
sudo grub


```

So now I'm in grub where I have something like the following session:

```

>find /boot/grub/stage1
(hd0,0)

>root (hd0,0)

>setup (hd0)
 Checking if ""/boot/grub/stage1" exists... yes
 Checking if ""/boot/grub/stage2" exists... yes
 Checking if ""/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"... 18 sectors are embedded.
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

```

But after this it still hangs at the "Loading stage1.5" message ?

At this point I should mention that I've also done the following:

1 Checked the BIOS boot sequence (and tried all combinations thereof)

2  Double checked that the UUID in the "/boot/grub/menu.lst" is the same as the UUID given for "/dev/sda1" by "blkid".

3  Booted from various live CDs and made sure the file system is good, that all required files are where they should be and retired the grub stuff above.

At this point I can only ask if anyone has got any ideas ?  Or should I just go back to LILO ? (this used to always work without a problem !)

Finally I have to wonder why there isn't a utility on a live CD which will install & configure grub for you ? (i.e. show menu, pick partition containing "/boot", pick where to install grub, utility sorts out the actual work for you)

It really is tedious doing it by hand and I've had endless problems with it over the years.

Cheers.

---

### Post by arrange on 2009-09-12
Could you please post the output of the [boot_info_script]("http://sourceforge.net/projects/bootinfoscript/") here?

---

### Post by Raptor Ramjet on 2009-09-12
Cheers for the link.  However since I posted I also tried creating a new partition and installing Ubuntu desktop to it (to see if it's installation of grub would work)

So now I have three partitions on the disk (Ubuntu desktop was installed to "/dev/sda3") but the output of the script is as follows:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000acdbc

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,937,037,374 1,937,037,312  83 Linux
/dev/sda2       1,949,327,100 1,953,520,064     4,192,965  82 Linux swap / Solaris
/dev/sda3    *  1,937,037,375 1,949,327,099    12,289,725  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="d78fe000-7286-4ddf-9899-6b37afa7b9d8" TYPE="reiserfs" 
/dev/sda2: UUID="550900ad-64e4-4608-b4de-1d30e74a901c" TYPE="swap" 
/dev/sda3: UUID="fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		5

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
# kopt=root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-386 root=UUID=d78fe000-7286-4ddf-9899-6b37afa7b9d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single
initrd		/boot/initrd.img-2.6.24-24-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.22-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.22-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single
initrd		/boot/initrd.img-2.6.22-16-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single
initrd		/boot/initrd.img-2.6.12-10-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.10-5-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386

title		Ubuntu 8.04.3 LTS, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single
initrd		/boot/initrd.img-2.6.10-5-386

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/hda1 -- converted during upgrade to edgy
#
# 2009/09/11 Comment out all entries for ATA disk.
#
#UUID=3b267028-8f02-4aea-b277-e443a9dbe9be	/	reiserfs notail 0 1
#
# 2009/09/11 Comment out all entries for ATA disk.
#
# /dev/hda5 -- converted during upgrade to edgy
#
#UUID=61b062bb-8326-4d6b-ad07-f0443d576674 none swap sw 0 0
#
# 2009/08/12 Added 1 Tb SATA disk on /dev/sda1.
#
# 2009/09/12 Disk ATA disk removed so sata drive is only disk.
#
UUID=d78fe000-7286-4ddf-9899-6b37afa7b9d8	/	reiserfs notail 0 1
#
# 2009/09/11 Added swap partition for move to new machine.
#
UUID=61b062bb-8326-4d6b-ad07-f0443d576674 none swap sw 0 0
#
# CDRom
#
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

=================== sda1: Location of files loaded by Grub: ===================


 792.3GB: boot/grub/menu.lst
 792.2GB: boot/grub/stage2
 792.3GB: boot/initrd.img-2.6.10-5-386
 792.3GB: boot/initrd.img-2.6.12-10-386
 792.3GB: boot/initrd.img-2.6.15-28-386
 792.3GB: boot/initrd.img-2.6.17-11-386
 792.3GB: boot/initrd.img-2.6.17-11-386.bak
 792.3GB: boot/initrd.img-2.6.20-16-386
 792.3GB: boot/initrd.img-2.6.20-16-386.bak
 792.3GB: boot/initrd.img-2.6.22-16-386
 792.3GB: boot/initrd.img-2.6.22-16-386.bak
 792.3GB: boot/initrd.img-2.6.24-24-386
 792.3GB: boot/initrd.img-2.6.24-24-386.bak
 792.3GB: boot/vmlinuz-2.6.10-5-386
 792.3GB: boot/vmlinuz-2.6.12-10-386
 792.3GB: boot/vmlinuz-2.6.15-28-386
 792.3GB: boot/vmlinuz-2.6.17-11-386
 792.3GB: boot/vmlinuz-2.6.20-16-386
 792.3GB: boot/vmlinuz-2.6.22-16-386
 792.3GB: boot/vmlinuz-2.6.24-24-386
 792.3GB: initrd.img
 792.3GB: initrd.img.old
 792.3GB: vmlinuz
 792.3GB: vmlinuz.old

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
# kopt=root=UUID=fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb

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
uuid		fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-386 root=UUID=d78fe000-7286-4ddf-9899-6b37afa7b9d8 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single 
initrd		/boot/initrd.img-2.6.24-24-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.22-16-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash 
initrd		/boot/initrd.img-2.6.22-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.22-16-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single 
initrd		/boot/initrd.img-2.6.22-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.20-16-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.20-16-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single 
initrd		/boot/initrd.img-2.6.20-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.17-11-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.17-11-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single 
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.15-28-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.15-28-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.12-10-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.12-10-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.10-5-386 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro quiet splash 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, kernel 2.6.10-5-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=UUID=3b267028-8f02-4aea-b277-e443a9dbe9be ro single 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=fba4805d-2ed9-46d0-bb7a-b3073a7f7ddb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=550900ad-64e4-4608-b4de-1d30e74a901c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 995.6GB: boot/grub/menu.lst
 995.6GB: boot/grub/stage2
 995.7GB: boot/initrd.img-2.6.28-11-generic
 995.8GB: boot/vmlinuz-2.6.28-11-generic
 995.7GB: initrd.img
 995.8GB: vmlinuz


```

Cheers again for the link.

---

### Post by arrange on 2009-09-12
Everything in the outputs looks OK to me. If noone comes up with a better idea, I would suggest creating [a dedicated /boot partition]("http://members.iinet.net/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_") towards the beginning of the drive, because it might be too far for the grub to reach for the stage2 file at 792.3GB.

Or - for more info look [here]("http://members.iinet.net/~herman546/p15.html#Grub_loading_stage1.5").

---

### Post by presence1960 on 2009-09-12
everything does look ok in the output of the script. usually though if the boot files are beyond the point which the BIOS can read you will get an error 18.

But I would give it a shot, or see if your manufacturer has a BIOS upgrade which will fix that problem.

You may have some type of problem with your disk. I had a clients machine do something similar and no matter what I did it would stop at that message. I wound up using [Dban]("http://www.dban.org/") to wipe the disk and the install worked after that.

---

### Post by Raptor Ramjet on 2009-09-15
Just to update everyone with my progress.

Over the weekend I moved my existing "/" partition "up" the disk so I could put in a 200 Mb "/boot" partition at the "start" of the disk.  And this took GParted nearly two days to finish (I started it off on Saturday at about 11:30 a.m. and it eventually finished at about 6:00 p.m. on Sunday)

Sadly though I still couldn't get Grub beyond the "stage1.5" message so I then took the advice about looking for a BIOS update, found such an update on the VIA site and applied it.  After this I wiped most of my directories (leaving only "/home") and reinstalled Ubuntu server from scratch but still using the new 200Mb partition for "/boot".

(n.b. All the data on the disk was already backed up before I started all this)

Following this the server boots perfectly so I reconfigured it by restoring my "/etc" configuration files from backups and it's been working fine ever since.

Best of all I also got a picopsu unit from ebay so it now runs almost silently (there's a single case fan in to get some airflow) and, according to my watt meter, it's only drawing around 26Watts most of the time.

So I'm not really sure if it was the BIOS update or the "/boot" partition that did the trick but all is well.

So thank you all for your assistance/suggestions.

---

### Post by presence1960 on 2009-09-15
> **Raptor Ramjet said:**
> Just to update everyone with my progress.

Over the weekend I moved my existing "/" partition "up" the disk so I could put in a 200 Mb "/boot" partition at the "start" of the disk.  And this took GParted nearly two days to finish (I started it off on Saturday at about 11:30 a.m. and it eventually finished at about 6:00 p.m. on Sunday)

Sadly though I still couldn't get Grub beyond the "stage1.5" message so I then took the advice about looking for a BIOS update, found such an update on the VIA site and applied it.  After this I wiped most of my directories (leaving only "/home") and reinstalled Ubuntu server from scratch but still using the new 200Mb partition for "/boot".

(n.b. All the data on the disk was already backed up before I started all this)

Following this the server boots perfectly so I reconfigured it by restoring my "/etc" configuration files from backups and it's been working fine ever since.

Best of all I also got a picopsu unit from ebay so it now runs almost silently (there's a single case fan in to get some airflow) and, according to my watt meter, it's only drawing around 26Watts most of the time.

So I'm not really sure if it was the BIOS update or the "/boot" partition that did the trick but all is well.

So thank you all for your assistance/suggestions.

Glad you got it working! Enjoy Ubuntu.

---

