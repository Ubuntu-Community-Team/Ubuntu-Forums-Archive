---
title: "Booting From External harddrive"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by verbal.kint on 2008-12-23
I have 7.10 installed on my internal hard drive, it was working fine until I installed 8.10 on a partition on my external hard drive. The grub loader was messed up and I ended up having to reinstall grub.....long story short I'm now able to boot into my 7.10 install fine.

The problem now is that I still can't boot into my 8.10 install. The external hard drive shows up on the boot menu but when I try to boot into it, it says a non system disk is inserted. I should probably say at this point that the external hard drive is partitioned into a FAT32 partition and an ext3 that the 8.10 is installed on.

I tried to set up the 8.10 partition as a virtual machine but when I turned it on it says FATAL:no bootable medium found.

any ideas?

---

### Post by uidb4056 on 2008-12-23
You must reinstall 8.10 on external HD, if using LiveCD be careful to choose advanced button after you have defined the partitions to use and **select to install GRUB in the external HD**. Then using the boot menu you should be able to boot 8.10 from the external HD.

---

### Post by verbal.kint on 2008-12-23
> **uidb4056 said:**
> You must reinstall 8.10 on external HD, if using LiveCD be careful to choose advanced button after you have defined the partitions to use and **select to install GRUB in the external HD**. Then using the boot menu you should be able to boot 8.10 from the external HD.

is this the only way to do it? i dont mind fiddling around at the command line if there is another way of doing it

---

### Post by uidb4056 on 2008-12-23
> **verbal.kint said:**
> is this the only way to do it? i dont mind fiddling around at the command line if there is another way of doing it

You can try this way [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by caljohnsmith on 2008-12-23
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be about booting 8.10.

---

### Post by verbal.kint on 2008-12-23
well done on the script, great idea!It's retard proof!! here are the results:
```
/dev/sdb has no valid partition table.
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdc and looks on boot drive #1 in partition #1 for its boot files.

sda1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 7.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2:
    File system:  Extended Partition

sda5:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda6:
    File system:  swap

sda7:
    File system:  ext2
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdc1:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdc2:
    File system:  ext3
    Boot sector  type:  Grub
    Boot sector  info:  Grub is installed to the boot sector of /dev/sdc2 and looks at sector 936345305 of the same hard drive for the stage2 file. (a stage2 file is at this location on /dev/sdc) and on partition #1 for menu.lst.
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29350754    14675346   83  Linux
/dev/sda2        29350755   156296384    63472815    5  Extended
/dev/sda5        48885795   156296384    53705295   83  Linux
/dev/sda6        29350881    33543719     2096419+  82  Linux swap / Solaris
/dev/sda7        33543783    48885794     7671006   83  Linux

Partition table entries are not in disk order

/dev/sda: OK


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea696c85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   913407704   456703821    b  W95 FAT32
/dev/sdc2       913407705   944123984    15358140   83  Linux

/dev/sda: OK
/dev/sdc: OK

/dev/sda1: UUID="499840b7-d5ea-4776-9542-8e45b7b569e8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="97db474d-d671-4785-8aa5-2bfac883a762" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="7cc2610f-d7e9-4ea2-b050-3d358a7e816b" 
/dev/sda7: UUID="8b53031d-6ff9-4016-a48e-86b6e862866d" TYPE="ext2" 
/dev/sdc1: LABEL="IOMEGA_HDD" UUID="4D70-7532" TYPE="vfat" 
/dev/sdc2: UUID="b8cc8b9f-57b3-4e62-999b-019bef29ff7e" SEC_TYPE="ext2" TYPE="ext3" 

sda1/boot/grub/menu.lst

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
# kopt=root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda5
UUID=97db474d-d671-4785-8aa5-2bfac883a762 /drive          ext3    defaults        0       2
# /dev/sda6
UUID=72d1a9d2-2c14-4a25-aefe-2bb9b42d5a68 none            swap    sw              0       0
# /dev/sda7
UUID=8b53031d-6ff9-4016-a48e-86b6e862866d /home/vinnie/Downloads ext2  defaults   0       3
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/sda5 /storage ext3 defaults 0 0

sda1/boot

total 53100
drwxr-xr-x  3 root root    4096 2008-12-09 19:05 .
drwxr-xr-x 24 root root    4096 2008-11-28 21:35 ..
-rw-r--r--  1 root root  417807 2008-02-12 04:30 abi-2.6.22-14-generic
-rw-r--r--  1 root root  417864 2008-10-22 01:51 abi-2.6.22-15-generic
-rw-r--r--  1 root root  417864 2008-11-24 19:35 abi-2.6.22-16-generic
-rw-r--r--  1 root root   67666 2008-02-12 04:30 config-2.6.22-14-generic
-rw-r--r--  1 root root   67655 2008-10-22 01:51 config-2.6.22-15-generic
-rw-r--r--  1 root root   67655 2008-11-24 19:35 config-2.6.22-16-generic
drwxr-xr-x  2 root root    4096 2008-12-23 19:44 grub
-rw-r--r--  1 root root 7373699 2008-05-27 00:33 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 7372586 2008-05-26 21:16 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root 7373290 2008-11-12 18:12 initrd.img-2.6.22-15-generic
-rw-r--r--  1 root root 7373400 2008-11-04 18:46 initrd.img-2.6.22-15-generic.bak
-rw-r--r--  1 root root 7372741 2008-12-09 19:05 initrd.img-2.6.22-16-generic
-rw-r--r--  1 root root 7373531 2008-11-30 22:19 initrd.img-2.6.22-16-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 12:03 memtest86+.bin
-rw-r--r--  1 root root 1052627 2008-02-12 04:30 System.map-2.6.22-14-generic
-rw-r--r--  1 root root 1053031 2008-10-22 01:51 System.map-2.6.22-15-generic
-rw-r--r--  1 root root 1053031 2008-11-24 19:35 System.map-2.6.22-16-generic
-rw-r--r--  1 root root 1743752 2008-02-12 04:30 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1743784 2008-10-22 01:51 vmlinuz-2.6.22-15-generic
-rw-r--r--  1 root root 1744072 2008-11-24 19:35 vmlinuz-2.6.22-16-generic

sda1/boot/grub

total 220
drwxr-xr-x 2 root root   4096 2008-12-23 19:44 .
drwxr-xr-x 3 root root   4096 2008-12-09 19:05 ..
-rw-r--r-- 1 root root    197 2008-12-23 19:44 default
-rw-r--r-- 1 root root     45 2008-12-23 19:43 device.map
-rw-r--r-- 1 root root   8660 2008-12-23 19:44 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-12-23 19:44 fat_stage1_5
-rw-r--r-- 1 root root     15 2008-12-23 19:44 installed-version
-rw-r--r-- 1 root root   9152 2008-12-23 19:44 jfs_stage1_5
-rw-r--r-- 1 root root   5121 2008-12-23 17:29 menu.lst
-rw-r--r-- 1 root root   5713 2008-12-23 17:24 menu.lst~
-rw-r--r-- 1 root root   7860 2008-12-23 19:44 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-12-23 19:44 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-23 19:44 stage1
-rw-r--r-- 1 root root 110292 2008-12-23 19:44 stage2
-rw-r--r-- 1 root root   9980 2008-12-23 19:44 xfs_stage1_5

sdc2/boot/grub/menu.lst

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
# kopt=root=UUID=b8cc8b9f-57b3-4e62-999b-019bef29ff7e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b8cc8b9f-57b3-4e62-999b-019bef29ff7e

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
uuid		b8cc8b9f-57b3-4e62-999b-019bef29ff7e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b8cc8b9f-57b3-4e62-999b-019bef29ff7e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b8cc8b9f-57b3-4e62-999b-019bef29ff7e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b8cc8b9f-57b3-4e62-999b-019bef29ff7e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b8cc8b9f-57b3-4e62-999b-019bef29ff7e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single 
initrd		/boot/initrd.img-2.6.22-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


sdc2/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=b8cc8b9f-57b3-4e62-999b-019bef29ff7e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7cc2610f-d7e9-4ea2-b050-3d358a7e816b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sdc2/boot

total 11948
drwxr-xr-x  3 root root    4096 2008-12-23 20:24 .
drwxr-xr-x 20 root root    4096 2008-12-23 20:24 ..
-rw-r--r--  1 root root  507665 2008-10-24 09:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 09:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-23 20:24 grub
-rw-r--r--  1 root root 8178518 2008-12-23 20:24 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 09:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 09:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 09:29 vmlinuz-2.6.27-7-generic

sdc2/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-23 20:24 .
drwxr-xr-x 3 root root   4096 2008-12-23 20:24 ..
-rw-r--r-- 1 root root    197 2008-12-23 20:24 default
-rw-r--r-- 1 root root     30 2008-12-23 20:24 device.map
-rw-r--r-- 1 root root   8108 2008-12-23 20:24 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-23 20:24 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-23 20:24 installed-version
-rw-r--r-- 1 root root   8712 2008-12-23 20:24 jfs_stage1_5
-rw-r--r-- 1 root root   6771 2008-12-23 20:24 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-23 20:24 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-23 20:24 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-23 20:24 stage1
-rw-r--r-- 1 root root 121460 2008-12-23 20:24 stage2
-rw-r--r-- 1 root root   9556 2008-12-23 20:24 xfs_stage1_5

StdErr Messages 

Unknown BootLoader  on /dev/sdc1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 8a 00  |.Z.MSWIN4.1..@..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  9a 7e 71 36 7f b3 01 00  00 00 00 00 02 00 00 00  |.~q6............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 32 75 70 4d 4e  4f 20 4e 41 4d 45 20 20  |..)2upMNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
hexdump: stdin: Illegal seek
```


I reinstalled the grub as per the instructions above and the grub would run when I booted from the external but the only options in the grub menu were 7.10 kernels when I tried to select any of them I just got a error 17. 

I then tried a complete reinstall, taking care to go into the advanced settings and select the correct partition (dev/sdc2) for the boot loader but the same thing happened with the grub (only 7.10 kernels). 

So that's where I'm at!!

---

### Post by caljohnsmith on 2008-12-23
Forum member meierfra is the one who wrote that handy script, so he deserves full credit for it. :) Do you have sda and sdb in a RAID configuration? It looks like you might. 

Have you tried booting the sda drive on start up? According the script it is configured correctly to boot Grub, and you should then be able to boot into 7.10 on that drive. The Grub in the MBR (Master Boot Record) of your sdc drive doesn't appear to be correctly configured though, so how about doing the following from your Intrepid CD (make sure to use Intrepid and not a 7.10 CD):
```
sudo grub
grub> root (hd2,1)
grub> setup (hd2)
grub> quit
```
Then try booting your sdc Intrepid drive, and you should get the Grub menu and be able to boot into Intrepid. But you will have to tweak your Intrepid's menu.lst slightly to boot your 7.10 install on the sda drive. How about seeing if you can get this far first, or let me know what problems you run into. We can work from there.

---

### Post by verbal.kint on 2008-12-23
I tried reinstalling the intrepid grub from the live cd and now when i try to boot from the external hard drive it gets stuck in a loop showing "Stage 1.5"

I noticed that sometimes my external hard drive shows up as sdb and sometimes sdc.

---

### Post by caljohnsmith on 2008-12-23
How about doing:
```
sudo fdisk -l
```
Determine whether Intrepid is on sdb or sdc, and then do:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Red"]sdc[/COLOR]
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
But change sdc above to sdb if the Intrepid drive is actually sdb. Please post the output of all the above commands, reboot, set your BIOS to boot the sdc drive, and let me know what happens.

---

### Post by verbal.kint on 2008-12-23
the fdisk command ( run from the intrepid live cd)
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1827    14675346   83  Linux
/dev/sda2            1828        9729    63472815    5  Extended
/dev/sda5            3044        9729    53705295   83  Linux
/dev/sda6            1828        2088     2096419+  82  Linux swap / Solaris
/dev/sda7            2089        3043     7671006   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea696c85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       56857   456703821    b  W95 FAT32
/dev/sdb2   *       56858       58769    15358140   83  Linux
```


the grub commands:
```
grub> device (hd1) /dev/sdb

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

still at the same situation, getting an infinite loop of "Stage 1.5" echoed onto the screen when booting from external

---

### Post by caljohnsmith on 2008-12-23
So you don't get a Grub error when booting the sdc drive, just a repeating "stage 1.5" on the screen? If that's true, I think you may have an issue with how the sdc drive is configured in your BIOS. How about going into your BIOS and look for settings for your sdc drive like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. For whichever settings you have, try changing them one-by-one and then booting the sdc drive again. I would recommend writing down any settings you change so you can revert back if necessary. Let me know how that goes.

---

