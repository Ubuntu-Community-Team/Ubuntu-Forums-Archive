---
title: "4 boot loaders installed - how to clean?"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by MartinHansell on 2009-02-10
Hi,

I have tinkered (a lot!) with getting my Linux box set up.  And the result is that I now have 4 disks each with a different boot loader on them.

I am not finished tinkering.  I want to reinstall Intrepid with lvm2, but first I want to clean the mbr's to avoid any conflicts when I install (which I have experienced already).

How do I go about getting rid of all unnecessary data/info in the mbr's for each disk which is not being used to boot up?

Thanks
Martin

Details are below... (ignore the sde drive, it's just a usb that is not normally there).

```


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc
 => Grub is installed in the MBR of /dev/sdd and looks on boot drive #-127 in 
    partition #1 for /.
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc2ce541e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006cbbf

Partition  Boot         Start           End          Size  Id System



Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00bd00bd

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   149,838,254   149,838,192  83 Linux
/dev/sdc2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdc5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02830282

Partition  Boot         Start           End          Size  Id System



Drive sde: _____________________________________________________________________

Disk /dev/sde: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders, total 512000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1ed6bcc

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32       511,487       511,456   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="08F06AA7F06A9B28" LABEL="Media" TYPE="ntfs" 
/dev/sdc1: UUID="9c11cf12-98e9-4e4b-a130-97775e812800" TYPE="ext3" 
/dev/sdc5: UUID="290f7016-646f-45fe-9641-c6948ad1e151" TYPE="swap" 
/dev/sde1: SEC_TYPE="msdos" UUID="30CF-3A8E" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mangoking/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mangoking)
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda1 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

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
# kopt=root=UUID=9c11cf12-98e9-4e4b-a130-97775e812800 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9c11cf12-98e9-4e4b-a130-97775e812800

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
uuid		9c11cf12-98e9-4e4b-a130-97775e812800
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c11cf12-98e9-4e4b-a130-97775e812800 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9c11cf12-98e9-4e4b-a130-97775e812800
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c11cf12-98e9-4e4b-a130-97775e812800 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9c11cf12-98e9-4e4b-a130-97775e812800
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=9c11cf12-98e9-4e4b-a130-97775e812800 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=290f7016-646f-45fe-9641-c6948ad1e151 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  41.5GB: boot/grub/menu.lst
  41.5GB: boot/grub/stage2
  41.5GB: boot/initrd.img-2.6.27-7-generic
  41.5GB: boot/vmlinuz-2.6.27-7-generic
  41.5GB: initrd.img
  41.5GB: vmlinuz


```

---

### Post by Ripose on 2009-02-10
I'm not sure but I think the SuperGrub Disk may help.
Go **[HERE]("http://www.supergrubdisk.org/")** and download from top right of page, CD or USB image.

---

### Post by MartinHansell on 2009-02-10
Thanks for your response Ripose.

Do I want to install Grub to the other disks?  Can I also use the SuperGrub disk to just wipe the mbr's back to the original state they were in when I first installed the disks?

Cheers.

---

### Post by caljohnsmith on 2009-02-10
> **MartinHansell said:**
> 
I am not finished tinkering.  I want to reinstall Intrepid with lvm2, but first I want to clean the mbr's to avoid any conflicts when I install (which I have experienced already).

How do I go about getting rid of all unnecessary data/info in the mbr's for each disk which is not being used to boot up?

What problems have you experienced that you are referring to?

---

