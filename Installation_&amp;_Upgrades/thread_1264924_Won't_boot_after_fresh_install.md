---
title: "Won't boot after fresh install"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by josesanders on 2009-09-12
I just did a fresh install of Ubuntu 9.04.  Everything seemed to go fine during the installation, but when I rebooted it never started up Ubuntu.  It just stuck at the hardware information screen that is displayed on bootup.  I have the following drives connected:

1 SATA HD formatted as follows during the installation:
100 GB ext3 partition, mount point is "/"
swap 8 GB (I've been told that this should be twice as big as the RAM, of which I have 4 GB)
Remaining space on this drive is a single ext3 partition with a mount point specified as /drv

In addition to the main HD I have a CD drive and an extra hard drive on the only IDE port.  The hard drive is set as slave, but it does have my old Ubuntu installation, and is bootable if set as master drive.

Any ideas?

---

### Post by lisati on 2009-09-12
My Compaq desktop has been known to get stuck after the BIOS splash screen from time to time. What sometimes works is entering BIOS setup (pressing F1 or some such key when the splash screen is showing) and then using the appropriate option to reset BIOS to its default settings.

---

### Post by presence1960 on 2009-09-12
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by josesanders on 2009-09-13
Here's what I get:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

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
Disk identifier: 0x38d1a392

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    74,364,884    74,364,822  83 Linux
/dev/sda2          74,364,885   154,256,129    79,891,245  83 Linux
/dev/sda3         154,256,130   156,296,384     2,040,255  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007e620

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   195,318,269   195,318,207  83 Linux
/dev/sdb2         195,318,270   976,768,064   781,449,795   5 Extended
/dev/sdb5         195,318,333   210,949,514    15,631,182  82 Linux swap / Solaris
/dev/sdb6         210,949,578   976,768,064   765,818,487  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f09323c1-1887-44fe-a399-20cb25bbca74" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="a55da239-c928-4ee6-b59d-e848dc930728" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="f30bbccf-0b5c-4d3b-ab62-b04c3065065f" TYPE="swap" 
/dev/sdb1: UUID="7a272b26-c4bc-4629-aa58-29966d934452" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="ce020a9c-a1b1-4902-89ea-497cb71c4a7e" TYPE="swap" 
/dev/sdb6: UUID="0081f18e-4c20-46cb-ba60-313d5dc195ef" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-17-lowlatency
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-17-lowlatency (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.20-17-lowlatency

title		Ubuntu, kernel 2.6.20-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu, kernel 2.6.20-16-lowlatency
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.20-16-lowlatency

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-lowlatency
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-lowlatency
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-lowlatency (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.20-15-lowlatency

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
#UUID=a55da239-c928-4ee6-b59d-e848dc930728 /               ext3    defaults,errors=remount-ro 0       1
#/dev/hda2 /media/hda2 ntfs-3g defaults,locale=en_US.utf8 0 0
#/dev/hda2 /storage ext3 defaults 0 0

# /dev/hda1
#UUID=EC7CC7DF7CC7A2A6 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#/dev/hda1 /storage ext3 defaults 0 0
/dev/hda1 /var/www/sharedmedia ext3 defaults 0 0

# /dev/hda3
UUID=f30bbccf-0b5c-4d3b-ab62-b04c3065065f none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda2: Location of files loaded by Grub: ===================


  74.6GB: boot/grub/menu.lst
  70.3GB: boot/grub/stage2
  70.3GB: boot/initrd.img-2.6.17-10-generic
  43.8GB: boot/initrd.img-2.6.17-11-generic
  43.3GB: boot/initrd.img-2.6.17-11-generic.bak
  43.9GB: boot/initrd.img-2.6.20-15-generic
  43.8GB: boot/initrd.img-2.6.20-15-generic.bak
  43.9GB: boot/initrd.img-2.6.20-15-lowlatency
  43.9GB: boot/initrd.img-2.6.20-15-lowlatency.bak
  43.0GB: boot/initrd.img-2.6.20-16-generic
  70.3GB: boot/initrd.img-2.6.20-16-generic.bak
  43.0GB: boot/initrd.img-2.6.20-16-lowlatency
  70.3GB: boot/initrd.img-2.6.20-16-lowlatency.bak
  43.0GB: boot/initrd.img-2.6.20-17-generic
  42.6GB: boot/initrd.img-2.6.20-17-lowlatency
  70.3GB: boot/vmlinuz-2.6.17-10-generic
  43.1GB: boot/vmlinuz-2.6.17-11-generic
  43.5GB: boot/vmlinuz-2.6.20-15-generic
  43.9GB: boot/vmlinuz-2.6.20-15-lowlatency
  43.0GB: boot/vmlinuz-2.6.20-16-generic
  70.3GB: boot/vmlinuz-2.6.20-16-lowlatency
  43.0GB: boot/vmlinuz-2.6.20-17-generic
  70.3GB: boot/vmlinuz-2.6.20-17-lowlatency
  42.6GB: initrd.img
  43.0GB: initrd.img.old
  70.3GB: vmlinuz
  43.0GB: vmlinuz.old

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
# kopt=root=UUID=7a272b26-c4bc-4629-aa58-29966d934452 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a272b26-c4bc-4629-aa58-29966d934452

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
uuid		7a272b26-c4bc-4629-aa58-29966d934452
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7a272b26-c4bc-4629-aa58-29966d934452 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7a272b26-c4bc-4629-aa58-29966d934452
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7a272b26-c4bc-4629-aa58-29966d934452 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7a272b26-c4bc-4629-aa58-29966d934452
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-17-lowlatency (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-17-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-17-lowlatency (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.20-17-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-17-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-17-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-lowlatency (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.20-16-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-lowlatency (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-lowlatency (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.20-15-lowlatency
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=a55da239-c928-4ee6-b59d-e848dc930728 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=7a272b26-c4bc-4629-aa58-29966d934452 /               ext3    relatime,errors=remount-ro 0       1
# /drv was on /dev/sdb6 during installation
UUID=0081f18e-4c20-46cb-ba60-313d5dc195ef /drv            ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=f30bbccf-0b5c-4d3b-ab62-b04c3065065f none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=ce020a9c-a1b1-4902-89ea-497cb71c4a7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  84.1GB: boot/grub/menu.lst
  84.2GB: boot/grub/stage2
  84.2GB: boot/initrd.img-2.6.28-11-generic
  84.1GB: boot/vmlinuz-2.6.28-11-generic
  84.2GB: initrd.img
  84.1GB: vmlinuz
```

The 500 GB drive is the one that I'm trying to boot from.

---

### Post by presence1960 on 2009-09-13
Everything looks good in the output from the script. Sorry I don't have any ideas, but it probably is BIOS related.

You mentioned your 80 Gb is not bootable but look at this:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb


```

either you are booting from the 80 GB or if you are booting from the 500 GB you have no bootloader installed. I would install GRUB onto the 500 GB MBR and then make sure the 500 GB is set to boot first in BIOS. To set grub up on MBR of 500 GB disk do this:
```

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Then reboot and go in BIOS and make sure your 500 GB disk is set to boot first in hard disk order.

---

### Post by josesanders on 2009-09-13
Thanks for the help presence1960.

I've gotten to step 4, and the output is as follows:

find /boot/grub/stage1
    (hd0,1)
    (hd1,0)

I'm not sure what to do next for step 5.  Should I use (hd1,0)?

Also, I have double-checked, and the bios is set to boot from the 500 GB drive.  The 80 GB drive is actually bootable, but that is my old Ubuntu installation from my previous computer.

---

### Post by presence1960 on 2009-09-13
> **josesanders said:**
> Thanks for the help presence1960.

I've gotten to step 4, and the output is as follows:

find /boot/grub/stage1
    (hd0,1)
    (hd1,0)

I'm not sure what to do next for step 5.  Should I use (hd1,0)?

Also, I have double-checked, and the bios is set to boot from the 500 GB drive.  The 80 GB drive is actually bootable, but that is my old Ubuntu installation from my previous computer.

Use (hd1,0) as this is your 9.04 install. Then use setup (hd1). exit, reboot and put your 500 GB disk as first boot in BIOS hard disk boot order. Just noticed your 500 Gb is set to boot, that is good!.

---

### Post by josesanders on 2009-09-13
Okay, that did it.  Thanks a lot.  Do you know what I did wrong during the install?

---

### Post by presence1960 on 2009-09-13
you placed GRUB on the wrong disk. You already had sdb booting first. You put GRUB on sda. Then when you boot you had no bootloader on sdb which is the drive that boots. You probably didn't even know that GRUB went on MBR of sda because that is the default on an Ubuntu install. If you click the Advanced tab on the Ready to install screen you can choose where to put GRUB. In your case since sdb is your first boot hard disk you would have chosen /dev/sdb. here is a screenshot of that Advanced tab for future reference.

---

### Post by mocadedhed on 2009-09-13
Presence1960 - do you have a quick link to how to install Grub - I've got a successful install of 9.04 on my laptop of 9.04, but didn't install the bootloader at all (don't ask me why). Now how do I install GRUB? Do you have a doc I can read up on? I've been trying the grub-install command, but am guessing that I'm not using the right syntax. (using live CD). I should add that "successful install of 9.04" is not totally accurate as now it won't boot at all (since I didn't install GRUB).
 
I'm entering ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
 
Thanks for any help.
 
Here are my RESULTS.txt from your script:
============================= Boot Info Summary: ==============================
 
=> No boot loader is installed in the MBR of /dev/sda
 
sda1: _________________________________________________________________________
 
File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 9.04
Boot files/dirs: /etc/fstab
 
sda2: _________________________________________________________________________
 
File system: Extended Partition
Boot sector type: -
Boot sector info: 
 
sda5: _________________________________________________________________________
 
File system: swap
Boot sector type: -
Boot sector info: 
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4
 
Partition Boot Start End Size Id System
 
/dev/sda1 63 114,286,409 114,286,347 83 Linux
/dev/sda2 114,286,410 117,210,239 2,923,830 5 Extended
/dev/sda5 114,286,473 117,210,239 2,923,767 82 Linux swap / Solaris
 
 
blkid -c /dev/null: ____________________________________________________________
 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6b401b91-2c17-4d81-8c37-bde7e022b974" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="2a6976be-d536-4d0e-b76c-aeb8a8bd0868" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
 
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
 
 
=============================== sda1/etc/fstab: ===============================
 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=6b401b91-2c17-4d81-8c37-bde7e022b974 / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=2a6976be-d536-4d0e-b76c-aeb8a8bd0868 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
 
=================== sda1: Location of files loaded by Grub: ===================
 
 
53.8GB: boot/initrd.img-2.6.28-11-generic
53.9GB: boot/vmlinuz-2.6.28-11-generic
53.8GB: initrd.img
53.9GB: vmlinuz

---

