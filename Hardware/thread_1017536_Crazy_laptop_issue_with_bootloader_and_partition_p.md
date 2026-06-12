---
title: "Crazy laptop issue with bootloader and partition problems"
date: 2008-12-21
forum: Hardware
---

### Post by Hydrothrax on 2008-12-21
Hello,

I've got a funky problem with my laptop. It was a dual-boot between windows XP and Ubuntu 8.04. I had added another partiton to it by installing 8.10 in 64-bit version, and being the stupid noob that I am, deleted the Ubuntu 8,04 partition without thinking, totally messing up my Grub bootloader. 

With a little too much messing around, I am now left with 2 Windows XP [my original one, XP Home Edition [on sda2], and XP pro in German......O.o] and 3 or 4 Ubuntu 8.10s, all in 64-bit. The windows XP Home Edition no longer starts [past the XP screen it is black, no pointer] and will only start in safe mode. The other XP is recognized by the Windows bootloader but doesn't work at all, and all my important data is on the XP Home partition. It cannot be accessed my my main Ubuntu partition [sda 11 and 12 I believe].

The Grub bootloader shows all the Ubuntu partitions and then a "Windows 98/2000/XP" bootloader [it used to only say XP or something like that] and then the windows bootloader comes [if I choose it] with two windows, one which is impossible to get to work [and I want it gone] and the othet being my original XP.

It gets even better. This laptop [Toshiba Satellite A215-S5837] is built for Vista. I hated it and got rid of it, putting XP on there and spending about 4-5 days getting all the drivers in XP. Then I added Ubuntu later.

I'm A US foreign exchange student in Germany, with no XP disks, an Ubuntu 8.10 64-bit install disk [downloaded] and no external hard drive or anything to store my data. My program install disks for my Windows programs are also all back in the US, so if I reformatted, I couldn't do much for the next 7 months. 

I wish Windows and windows programs were as easily accessible as Linux...........

Anyone out there who knows what I can do? I'm not a complete noob with computers, but can't program yet, and everything I know is through excessive tinkering....XD

I'd REALLY appreciate the help!

-Hydro

---

### Post by caljohnsmith on 2008-12-21
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by Hydrothrax on 2008-12-23
[sorry for the late reply! D8]

```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #13 for its boot files.

sda1:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda10:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda11:
    File system:  swap

sda12:
    File system:  swap

sda13:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda14:
    File system:  swap

sda2:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3:
    File system:  Extended Partition

sda5:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0

sda6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda8:
    File system:  swap

sda9:
    File system:  swap


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe21d56ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    76511547    36718750    7  HPFS/NTFS
/dev/sda3        76517595   312576704   118029555    f  W95 Ext'd (LBA)
/dev/sda5       106735923   116503379     4883728+   7  HPFS/NTFS
/dev/sda6       116503443   125049959     4273258+  83  Linux
/dev/sda7       218210958   227367944     4578493+  83  Linux
/dev/sda8       227368008   229761629     1196811   82  Linux swap / Solaris
/dev/sda9       229761693   234677519     2457913+  82  Linux swap / Solaris
/dev/sda10      251160273   301154489    24997108+  83  Linux
/dev/sda11      301154553   304110449     1477948+  82  Linux swap / Solaris
/dev/sda12      304110513   312576704     4233096   82  Linux swap / Solaris
/dev/sda13       76517721   105370334    14426307   83  Linux
/dev/sda14      105370398   106735859      682731   82  Linux swap / Solaris

Partition table entries are not in disk order

Warning: partition 1 does not end at a cylinder boundary

/dev/sda1: UUID="28A89DDFA89DABB6" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="E09CC0B99CC08B8A" LABEL="BasWINDOWS" TYPE="ntfs" 
/dev/sda5: UUID="78E8C16FE8C12BE6" LABEL="BasDATA" TYPE="ntfs" 
/dev/sda6: UUID="3cf5f0f2-2931-4e31-b18a-fe48353e2618" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="7d0700e3-3833-42a0-85b5-a7fcfd0607b5" TYPE="swap" 
/dev/sda9: UUID="1953a983-6339-48b3-b88a-25c76a971d34" TYPE="swap" 
/dev/sda10: UUID="ac8a5550-96d0-4cbc-af90-fa81c821434a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="26c87295-fb50-46d6-a7e6-3aa1176d603f" TYPE="swap" 
/dev/sda12: UUID="3f1d249a-3528-4afb-a53d-7272d9c3633d" TYPE="swap" 
/dev/sda13: UUID="059b2415-281d-4a02-9202-18e87a2a1644" TYPE="ext3" 
/dev/sda14: UUID="22a16930-78f1-4ce1-a05d-6c598e6b1c30" TYPE="swap" 

sda10/boot/grub/menu.lst

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
# kopt=root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac8a5550-96d0-4cbc-af90-fa81c821434a

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
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-12-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-12-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda10/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1dde6d6e-3442-401a-af36-a864cff92a78 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda10/boot

total 12792
drwxr-xr-x  3 root root    4096 2008-11-26 11:32 .
drwxr-xr-x 21 root root    4096 2008-12-22 07:45 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-22 07:45 grub
-rw-r--r--  1 root root 8630005 2008-11-26 11:32 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic

sda10/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-22 07:45 .
drwxr-xr-x 3 root root   4096 2008-11-26 11:32 ..
-rw-r--r-- 1 root root    197 2008-11-29 11:10 default
-rw-r--r-- 1 root root     15 2008-11-29 11:10 device.map
-rw-r--r-- 1 root root   8108 2008-11-29 11:10 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-29 11:10 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-18 12:29 installed-version
-rw-r--r-- 1 root root   8712 2008-11-29 11:10 jfs_stage1_5
-rw-r--r-- 1 root root   6971 2008-11-26 11:29 menu.lst
-rw-r--r-- 1 root root   6971 2008-11-26 11:29 menu.lst~
-rw-r--r-- 1 root root   7352 2008-11-29 11:10 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-29 11:10 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-29 11:10 stage1
-rw-r--r-- 1 root root 121460 2008-11-29 11:10 stage2
-rw-r--r-- 1 root root   9556 2008-11-29 11:10 xfs_stage1_5

sda13/boot/grub/menu.lst

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
# kopt=root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=059b2415-281d-4a02-9202-18e87a2a1644

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
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, memtest86+ (on /dev/sda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda13/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda13
UUID=059b2415-281d-4a02-9202-18e87a2a1644 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda14
UUID=22a16930-78f1-4ce1-a05d-6c598e6b1c30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda13/boot

total 25508
drwxr-xr-x  3 root root    4096 2008-12-20 13:55 .
drwxr-xr-x 21 root root    4096 2008-12-20 14:20 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-20 13:54 grub
-rw-r--r--  1 root root 8660919 2008-12-20 13:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8661204 2008-12-20 13:55 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

sda13/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-20 13:54 .
drwxr-xr-x 3 root root   4096 2008-12-20 13:55 ..
-rw-r--r-- 1 root root    197 2008-12-20 10:20 default
-rw-r--r-- 1 root root     15 2008-12-20 10:20 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 10:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 10:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 10:20 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 10:20 jfs_stage1_5
-rw-r--r-- 1 root root   7857 2008-12-20 13:54 menu.lst
-rw-r--r-- 1 root root   7773 2008-12-20 13:54 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-20 10:20 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 10:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 10:20 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 10:20 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 10:20 xfs_stage1_5

sda6/boot/grub/menu.lst

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
# kopt=root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3cf5f0f2-2931-4e31-b18a-fe48353e2618

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
uuid		3cf5f0f2-2931-4e31-b18a-fe48353e2618
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3cf5f0f2-2931-4e31-b18a-fe48353e2618
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3cf5f0f2-2931-4e31-b18a-fe48353e2618
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=76e7fce5-0f30-476b-a655-4b339c371764 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda6/boot

total 12804
drwxr-xr-x  3 root root    4096 2008-11-29 11:50 .
drwxr-xr-x 20 root root    4096 2008-12-22 10:26 ..
-rw-r--r--  1 root root  503560 2008-10-24 02:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 02:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-06 06:43 grub
-rw-r--r--  1 root root 8641483 2008-11-29 11:49 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 02:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 02:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 02:55 vmlinuz-2.6.27-7-generic

sda6/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-06 06:43 .
drwxr-xr-x 3 root root   4096 2008-11-29 11:50 ..
-rw-r--r-- 1 root root    197 2008-12-06 06:43 default
-rw-r--r-- 1 root root     45 2008-12-06 06:43 device.map
-rw-r--r-- 1 root root   8108 2008-12-06 06:43 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-06 06:43 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-29 11:50 installed-version
-rw-r--r-- 1 root root   8712 2008-12-06 06:43 jfs_stage1_5
-rw-r--r-- 1 root root   5539 2008-11-29 11:50 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-06 06:43 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-06 06:43 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-06 06:43 stage1
-rw-r--r-- 1 root root 121460 2008-12-06 06:43 stage2
-rw-r--r-- 1 root root   9556 2008-12-06 06:43 xfs_stage1_5

sda7/boot/grub/menu.lst

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
# kopt=root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3

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
uuid		e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, memtest86+ (on /dev/sda8)
root		(hd0,7)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda7/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda12
UUID=dc14f144-c290-472c-877b-1bd8bc26b6a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda7/boot

total 12804
drwxr-xr-x  3 root root    4096 2008-12-07 04:54 .
drwxr-xr-x 20 root root    4096 2008-12-22 09:50 ..
-rw-r--r--  1 root root  503560 2008-10-24 02:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 02:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-07 04:55 grub
-rw-r--r--  1 root root 8642124 2008-12-07 04:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 02:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 02:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 02:55 vmlinuz-2.6.27-7-generic

sda7/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-07 04:55 .
drwxr-xr-x 3 root root   4096 2008-12-07 04:54 ..
-rw-r--r-- 1 root root    197 2008-12-07 04:54 default
-rw-r--r-- 1 root root     15 2008-12-07 04:54 device.map
-rw-r--r-- 1 root root   8108 2008-12-07 04:54 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-07 04:54 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-07 04:55 installed-version
-rw-r--r-- 1 root root   8712 2008-12-07 04:54 jfs_stage1_5
-rw-r--r-- 1 root root   6451 2008-12-07 04:55 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-07 04:54 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-07 04:54 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-07 04:54 stage1
-rw-r--r-- 1 root root 121460 2008-12-07 04:55 stage2
-rw-r--r-- 1 root root   9556 2008-12-07 04:54 xfs_stage1_5

StdErr Messages
```

looks....funky. O.o

---

### Post by caljohnsmith on 2008-12-23
OK, so you definitely have multiple Ubuntu installs, and also your Windows partitions are not mounting like you said. How about beginning by doing:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
sudo ntfsfix /dev/sda5
```
Please post the output of the ntfsfix commands, and if the ntfsfix commands say they completed successfully, then do:
```
sudo mkdir /media/sda2 /media/sda5
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda5 /media/sda5
ls -l /media/sda2 /media/sda5
nautilus /media &
```
Please post the output of all the above commands, and if all goes well, you should be able to browse your two Windows partitions with that last command. See if you can get that far, or let me know what problems you run into. :)

---

### Post by Hydrothrax on 2008-12-23
```
Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
darkfire@Basilisk:~$ sudo ntfsfix /dev/sda2
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.

```

```
Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
darkfire@Basilisk:~$ sudo ntfsfix /dev/sda2
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.
darkfire@Basilisk:~$ sudo ntfsfix /dev/sda5
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.
darkfire@Basilisk:~$ 

```

and the second part:

```
darkfire@Basilisk:~$ sudo mkdir /media/sda2 /media/sda5
mkdir: cannot create directory `/media/sda2': File exists
mkdir: cannot create directory `/media/sda5': File exists
darkfire@Basilisk:~$ sudo mount /dev/sda2 /media/sda2
darkfire@Basilisk:~$ sudo mount /dev/sda5 /media/sda5
darkfire@Basilisk:~$ ls -l /media/sda2 /media/sda4
ls: cannot access /media/sda4: No such file or directory
/media/sda2:
total 2623
-rwxrwxrwx 2 root root       0 2008-12-11 07:58 -1665102966
-rwxrwxrwx 1 root root  150528 2004-11-11 06:00 arcldr.exe
-rwxrwxrwx 1 root root  163840 2004-11-11 06:00 arcsetup.exe
drwxrwxrwx 1 root root       0 2008-06-30 20:09 ATI
-rwxrwxrwx 1 root root       0 2008-06-30 19:59 AUTOEXEC.BAT
-rwxrwxrwx 1 root root    4952 2004-11-11 06:00 bootfont.bin
-rwxrwxrwx 1 root root     324 2008-12-20 08:44 boot.ini
-rwxrwxrwx 1 root root     484 2008-09-21 11:29 CDFE.log
-rwxrwxrwx 1 root root       0 2008-06-30 19:59 CONFIG.SYS
drwxrwxrwx 1 root root    4096 2008-10-12 06:34 Documents and Settings
drwxrwxrwx 1 root root       0 2008-12-20 07:51 Dokumente und Einstellungen
drwxrwxrwx 1 root root       0 2008-06-30 20:08 DRIVERS
-rwxrwxrwx 1 root root   13312 2008-12-11 07:58 exmucmf.exe
-rwxrwxrwx 1 root root    8192 2008-12-11 07:58 ftsuih.exe
drwxrwxrwx 1 root root       0 2008-07-24 09:54 Graphics
-rwxrwxrwx 1 root root     164 2008-07-03 02:25 install.dat
-rwxrwxrwx 1 root root       0 2008-06-30 19:59 IO.SYS
-rwxrwxrwx 1 root root     446 2008-07-01 20:44 IPH.PH
-rwxrwxrwx 1 root root       0 2008-09-12 00:11 lxcefire.000
-rwxrwxrwx 1 root root       0 2008-09-21 11:28 lxcefire.csv
-rwxrwxrwx 1 root root     867 2008-09-12 00:12 LXCEINST.000
-rwxrwxrwx 1 root root     867 2008-09-21 11:29 LXCEINST.csv
-rwxrwxrwx 1 root root    1164 2008-12-04 02:59 lxce.log
-rwxrwxrwx 1 root root    6394 2008-11-29 03:15 lxcescan.log
-rwxrwxrwx 1 root root 1912129 2008-09-20 12:38 lxceUNST.csv
-rwxrwxrwx 1 root root       0 2008-06-30 19:59 MSDOS.SYS
drwxrwxrwx 1 root root       0 2008-07-02 10:21 MSOCache
-rwxrwxrwx 1 root root   47564 2004-11-11 06:00 NTDETECT.COM
-rwxrwxrwx 1 root root  251184 2004-11-11 06:00 ntldr
drwxrwxrwx 1 root root       0 2008-09-25 04:34 ProgramData
drwxrwxrwx 1 root root   16384 2008-12-11 08:00 Program Files
drwxrwxrwx 1 root root       0 2008-06-30 20:06 RECYCLER
drwxrwxrwx 1 root root       0 2008-07-01 16:29 Sierra
drwxrwxrwx 1 root root       0 2008-09-18 01:22 System32
drwxrwxrwx 1 root root    4096 2008-12-06 23:25 System Volume Information
drwxrwxrwx 1 root root       0 2008-09-12 00:11 temp
drwxrwxrwx 1 root root       0 2008-06-30 22:22 TOSHIBA
drwxrwxrwx 1 root root       0 2008-08-09 15:53 VundoFix Backups
-rwxrwxrwx 1 root root     373 2008-10-02 22:46 VundoFix.txt
drwxrwxrwx 1 root root   61440 2008-12-20 04:23 WINDOWS
drwxrwxrwx 1 root root   12288 2008-12-11 06:38 $WIN_NT$.~BT
drwxrwxrwx 1 root root       0 2008-07-23 19:48 WTablet
darkfire@Basilisk:~$ nautilus /media &
[1] 8385
darkfire@Basilisk:~$ 

```


I can access windows again! THX! one problem solved :)

---

### Post by caljohnsmith on 2008-12-23
OK, so if you browse the /media/sda2 and /media/sda5 directories, it looks like you should have access to all your Windows files there. That should enable you to at least access all your Windows documents at this point. But about getting Windows to boot, you will most likely need a Windows Install CD to help fix those types of problems. As one more check though, please post the output of:
```
cat /media/sda2/boot.ini
```

---

### Post by Hydrothrax on 2008-12-23
```
darkfire@Basilisk:~$ cat /media/sda2/boot.ini
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.1
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.1="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
darkfire@Basilisk:~$ 
```

I JUST had that file open, LOL! BTW is there a way to make the windows bootloader only load one windows, so I can get rid of the other?

and is it possible to get rid of the other Ubuntu partitions while keeping the one that I'm on, and not screw up the Grub loader?

---

### Post by caljohnsmith on 2008-12-23
You mentioned in your first post that you couldn't boot into your sda2 Windows partition without using safe mode, so how about modifying your boot.ini file to try and boot the sda5 Windows parition:
```
gksudo gedit /media/sda2/boot.ini
```
And then change it as follows:
```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.1
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.1="Microsoft Windows XP Home Edition [COLOR="Blue"]sda2[/COLOR]" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](3)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition [COLOR="Blue"]sda5[/COLOR]" /fastdetect /NoExecute=OptIn

```
Reboot, and see if you can boot into the sda5 Windows install from the Windows boot menu. Let me know how it goes.

---

### Post by Hydrothrax on 2008-12-23
Booting into sda5 doesn't work...and I just tried it to prove it XD

The windows itself on there was never really a fully working system. T'was an experimental side-install to get the windows bootloader back. The original idea was to get rid of that partition [somehow] when everything was back to normal XD

In my original windows, it always boots to the XP loading screen, then goes black. No pointer, no blinking lights, nothing.

---

### Post by caljohnsmith on 2008-12-23
At least you can access your Windows files now, but based on the symptoms you get when booting Windows, I think you'll probably need a Windows Install CD in order to fix Windows. If you want to delete any of your Ubuntu partitions, that should be OK, but there's a good chance you will have to reinstall Grub to the MBR and point Grub to whichever is the remaining Ubuntu partition. You can do that with:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes.

---

### Post by Hydrothrax on 2008-12-23
So I just delete the extra partitions in gparted [I run it from my main ubuntu installation] and then run the code? 

(I don't want to make any stupid mistakes...last time I crashed GRUB and nothing worked XD)

---

### Post by caljohnsmith on 2008-12-23
> **Hydrothrax said:**
> So I just delete the extra partitions in gparted [I run it from my main ubuntu installation] and then run the code? 

(I don't want to make any stupid mistakes...last time I crashed GRUB and nothing worked XD)
Yes, and it would be best to delete those partitions from your Live CD, not while you are booted into one of your partitions, or you will run into problems. When you use the partition editor gparted (System > Admin > Partition Editor), right-click each of your swap partitions and select "swapoff". Then you should be able to delete the partitions you want to. After you are done, run the Grub commands from my previous post, and you should be OK.

---

### Post by Hydrothrax on 2008-12-23
but I don;t think I can boot from my Ubuntu 8.10 CD....or I just don't know how to O.o 

What kinds of problems would I have if I did it from a partition?

---

### Post by caljohnsmith on 2008-12-23
> **Hydrothrax said:**
> but I don;t think I can boot from my Ubuntu 8.10 CD....or I just don't know how to O.o 

What kinds of problems would I have if I did it from a partition?
How did you install Ubuntu? Did you use a Live CD? I would definitely not recommend making any partition changes unless you have a Live CD that you can boot in case something doesn't work quite right.

---

### Post by Hydrothrax on 2008-12-23
I downloaded the CD to install the 64-bit version of Ubuntu .10. I DO have a Knoppix disk somewhere that works, would that do?

---

### Post by caljohnsmith on 2008-12-23
> **Hydrothrax said:**
> I downloaded the CD to install the 64-bit version of Ubuntu .10. I DO have a Knoppix disk somewhere that works, would that do?
I think it would be safer to have the Intrepid Live CD since we don't know if the Grub version that comes with the Knoppix CD is recent enough to be compatible with Intrepid's new ext3 partitions. It is possible to pull tricks such as chrooting or downloading the newer Grub package, but I still think you would be safer with an Intrepid CD in case other issues come up too.

---

### Post by Hydrothrax on 2008-12-24
Got me a Live CD. Followed your codes.

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition
grub> 


```

*eye twitch* did I do something wrong? [has the terminal still open]

---

### Post by caljohnsmith on 2008-12-24
Often that type of error in the Grub command line is due to a corrupted partition table. How about re-running the script from post #2 and post the results of your new setup, and we can work from there.

---

### Post by Hydrothrax on 2008-12-24
```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #256 for its boot files.

sda1:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda10:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda13:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3:
    File system:  Extended Partition

sda7:
    File system:  swap


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe21d56ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    76511547    36718750    7  HPFS/NTFS
/dev/sda3        76517595   312576704   118029555    f  W95 Ext'd (LBA)
/dev/sda5       151091325   312576704    80742690    7  HPFS/NTFS
/dev/sda6        76517721   149725799    36604039+  83  Linux
/dev/sda7       149725863   151091324      682731   82  Linux swap / Solaris

Partition table entries are not in disk order

Warning: partition 1 does not end at a cylinder boundary

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
/dev/sda13 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda13 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda10 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)

/dev/sda1: UUID="28A89DDFA89DABB6" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="E09CC0B99CC08B8A" LABEL="BasWINDOWS" TYPE="ntfs" 
/dev/sda7: UUID="d12198fd-b0d6-4f8e-9a26-462614a03cb7" TYPE="swap" 
/dev/sda10: UUID="ac8a5550-96d0-4cbc-af90-fa81c821434a" TYPE="ext3" 
/dev/sda13: UUID="059b2415-281d-4a02-9202-18e87a2a1644" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

sda10/boot/grub/menu.lst

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
# kopt=root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac8a5550-96d0-4cbc-af90-fa81c821434a

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
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-12-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-12-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda10/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1dde6d6e-3442-401a-af36-a864cff92a78 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda10/boot

total 12792
drwxr-xr-x  3 root root    4096 2008-11-26 17:32 .
drwxr-xr-x 21 root root    4096 2008-12-22 13:45 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-22 13:45 grub
-rw-r--r--  1 root root 8630005 2008-11-26 17:32 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic

sda10/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-22 13:45 .
drwxr-xr-x 3 root root   4096 2008-11-26 17:32 ..
-rw-r--r-- 1 root root    197 2008-11-29 17:10 default
-rw-r--r-- 1 root root     15 2008-11-29 17:10 device.map
-rw-r--r-- 1 root root   8108 2008-11-29 17:10 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-29 17:10 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-18 18:29 installed-version
-rw-r--r-- 1 root root   8712 2008-11-29 17:10 jfs_stage1_5
-rw-r--r-- 1 root root   6971 2008-11-26 17:29 menu.lst
-rw-r--r-- 1 root root   6971 2008-11-26 17:29 menu.lst~
-rw-r--r-- 1 root root   7352 2008-11-29 17:10 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-29 17:10 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-29 17:10 stage1
-rw-r--r-- 1 root root 121460 2008-11-29 17:10 stage2
-rw-r--r-- 1 root root   9556 2008-11-29 17:10 xfs_stage1_5

sda13/boot/grub/menu.lst

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
# kopt=root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=059b2415-281d-4a02-9202-18e87a2a1644

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
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, memtest86+ (on /dev/sda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda13/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda13
UUID=059b2415-281d-4a02-9202-18e87a2a1644 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda14
UUID=22a16930-78f1-4ce1-a05d-6c598e6b1c30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda13/boot

total 25508
drwxr-xr-x  3 root root    4096 2008-12-20 19:55 .
drwxr-xr-x 21 root root    4096 2008-12-20 20:20 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-20 19:54 grub
-rw-r--r--  1 root root 8660919 2008-12-20 19:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8661204 2008-12-20 19:55 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

sda13/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-20 19:54 .
drwxr-xr-x 3 root root   4096 2008-12-20 19:55 ..
-rw-r--r-- 1 root root    197 2008-12-20 16:20 default
-rw-r--r-- 1 root root     15 2008-12-20 16:20 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 16:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 16:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 16:20 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 16:20 jfs_stage1_5
-rw-r--r-- 1 root root   7857 2008-12-20 19:54 menu.lst
-rw-r--r-- 1 root root   7773 2008-12-20 19:54 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-20 16:20 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 16:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 16:20 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 16:20 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 16:20 xfs_stage1_5

StdErr Messages 


sfdisk: 10: no such partition
boot_info_script.txt: line 236: [: =: unary operator expected
boot_info_script.txt: line 236: [: =: unary operator expected

sfdisk: 13: no such partition
boot_info_script.txt: line 236: [: =: unary operator expected
boot_info_script.txt: line 236: [: =: unary operator expected
```

---

### Post by caljohnsmith on 2008-12-24
> **Hydrothrax said:**
> ```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe21d56ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    76511547    36718750    7  HPFS/NTFS
/dev/sda3        76517595   312576704   118029555    f  W95 Ext'd (LBA)
/dev/sda5       [COLOR="Red"]151091325[/COLOR]   312576704    80742690    7  HPFS/NTFS
/dev/sda6        76517721   149725799    36604039+  83  Linux
/dev/sda7       149725863   [COLOR="Red"]151091324[/COLOR]      682731   82  Linux swap / Solaris

```
I'm not sure what happened with your repartitioning, but your sda5 NTFS partition now starts at the sector immediately after the sda7 partition, which is not good; since sda5 and sda7 are both logical partitions, there needs to be at least 64 sectors difference between the end of sda7 and the start of sda5. It looks to me like sda5 should actually be a primary partition, not a logical one. But that would explain why you couldn't run those Grub commands, because your partition table is basically corrupt at this point. 

Also, do you know why you can't mount your NTFS partitions again? They are marked as having an "unclean shutdown" again, and I'm just wondering if that is a common occurence with your setup? How about first making sure you reboot the Live CD, and then do:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
sudo ntfsfix /dev/sda5
sudo mkdir /media/sda2 /media/sda5 /media/sda6
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda5 /media/sda5
sudo mount /dev/sda6 /media/sda6
ls -l /media/sda2 /media/sda5 /media/sda6
sudo blkid
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```
And please post the output of all the above commands.

---

### Post by Hydrothrax on 2008-12-24
```
ubuntu@ubuntu:~$ sudo apt-get install ntfsprogs

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda2

Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda5
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.
ubuntu@ubuntu:~$ sudo mkdir /media/sda2 /media/sda5 /media/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/sda2
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/sda6
ubuntu@ubuntu:~$ ls -l /media/sda2 /media/sda5 /media/sda6
/media/sda2:
total 2623
-rwxrwxrwx 2 root root       0 2008-12-11 13:58 -1665102966
-rwxrwxrwx 1 root root  150528 2004-11-11 12:00 arcldr.exe
-rwxrwxrwx 1 root root  163840 2004-11-11 12:00 arcsetup.exe
drwxrwxrwx 1 root root       0 2008-07-01 01:09 ATI
-rwxrwxrwx 1 root root       0 2008-07-01 00:59 AUTOEXEC.BAT
-rwxrwxrwx 1 root root    4952 2004-11-11 12:00 bootfont.bin
-rwxrwxrwx 1 root root     324 2008-12-20 14:44 boot.ini
-rwxrwxrwx 1 root root     484 2008-09-21 16:29 CDFE.log
-rwxrwxrwx 1 root root       0 2008-07-01 00:59 CONFIG.SYS
drwxrwxrwx 1 root root    4096 2008-10-12 11:34 Documents and Settings
drwxrwxrwx 1 root root       0 2008-07-01 01:08 DRIVERS
-rwxrwxrwx 1 root root   13312 2008-12-11 13:58 exmucmf.exe
-rwxrwxrwx 1 root root    8192 2008-12-11 13:58 ftsuih.exe
drwxrwxrwx 1 root root       0 2008-07-24 14:54 Graphics
-rwxrwxrwx 1 root root     164 2008-07-03 07:25 install.dat
-rwxrwxrwx 1 root root       0 2008-07-01 00:59 IO.SYS
-rwxrwxrwx 1 root root     446 2008-07-02 01:44 IPH.PH
-rwxrwxrwx 1 root root       0 2008-09-12 05:11 lxcefire.000
-rwxrwxrwx 1 root root       0 2008-09-21 16:28 lxcefire.csv
-rwxrwxrwx 1 root root     867 2008-09-12 05:12 LXCEINST.000
-rwxrwxrwx 1 root root     867 2008-09-21 16:29 LXCEINST.csv
-rwxrwxrwx 1 root root    1164 2008-12-04 08:59 lxce.log
-rwxrwxrwx 1 root root    6394 2008-11-29 09:15 lxcescan.log
-rwxrwxrwx 1 root root 1912129 2008-09-20 17:38 lxceUNST.csv
-rwxrwxrwx 1 root root       0 2008-07-01 00:59 MSDOS.SYS
drwxrwxrwx 1 root root       0 2008-07-02 15:21 MSOCache
-rwxrwxrwx 1 root root   47564 2004-11-11 12:00 NTDETECT.COM
-rwxrwxrwx 1 root root  251184 2004-11-11 12:00 ntldr
drwxrwxrwx 1 root root       0 2008-09-25 09:34 ProgramData
drwxrwxrwx 1 root root   16384 2008-12-11 14:00 Program Files
drwxrwxrwx 1 root root       0 2008-07-01 01:06 RECYCLER
drwxrwxrwx 1 root root       0 2008-07-01 21:29 Sierra
drwxrwxrwx 1 root root       0 2008-09-18 06:22 System32
drwxrwxrwx 1 root root    4096 2008-12-07 05:25 System Volume Information
drwxrwxrwx 1 root root       0 2008-09-12 05:11 temp
drwxrwxrwx 1 root root       0 2008-07-01 03:22 TOSHIBA
drwxrwxrwx 1 root root       0 2008-08-09 20:53 VundoFix Backups
-rwxrwxrwx 1 root root     373 2008-10-03 03:46 VundoFix.txt
drwxrwxrwx 1 root root   61440 2008-12-20 10:23 WINDOWS
drwxrwxrwx 1 root root   12288 2008-12-11 12:38 $WIN_NT$.~BT
drwxrwxrwx 1 root root       0 2008-07-24 00:48 WTablet

/media/sda5:
total 44
drwxrwxrwx 1 root root  4096 2008-12-07 12:43 Dokumente und Einstellungen
drwxrwxrwx 1 root root  4096 2008-12-11 13:45 My Documents
drwxrwxrwx 1 root root  4096 2008-12-07 12:43 Programme
drwxrwxrwx 1 root root     0 2008-12-07 12:57 RECYCLER
drwxrwxrwx 1 root root  4096 2008-12-07 12:42 System Volume Information
drwxrwxrwx 1 root root 28672 2008-12-07 12:43 WINDOWS

/media/sda6:
total 96
drwxr-xr-x   2 root root  4096 2008-12-20 19:48 bin
drwxr-xr-x   3 root root  4096 2008-12-20 19:55 boot
lrwxrwxrwx   1 root root    11 2008-12-20 15:51 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-12-20 16:21 dev
drwxr-xr-x 125 root root 12288 2008-12-24 11:22 etc
drwxr-xr-x   3 root root  4096 2008-12-20 16:21 home
lrwxrwxrwx   1 root root    32 2008-12-20 19:54 initrd.img -> boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 root root    32 2008-12-20 15:54 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root  4096 2008-12-20 20:20 lib
drwxr-xr-x   4 root root  4096 2008-12-20 20:20 lib32
lrwxrwxrwx   1 root root     4 2008-12-20 15:52 lib64 -> /lib
drwx------   2 root root 16384 2008-12-20 15:51 lost+found
drwxr-xr-x   5 root root  4096 2008-12-24 09:52 media
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 mnt
drwxr-xr-x   2 root root  4096 2008-12-20 15:52 opt
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 proc
drwxr-xr-x  11 root root  4096 2008-12-23 20:57 root
drwxr-xr-x   2 root root  4096 2008-12-23 17:56 sbin
drwxr-xr-x   2 root root  4096 2008-12-20 15:52 srv
drwxr-xr-x   2 root root  4096 2008-10-14 13:02 sys
drwxrwxrwt  11 root root  4096 2008-12-24 11:22 tmp
drwxr-xr-x  12 root root  4096 2008-12-20 20:20 usr
drwxr-xr-x  15 root root  4096 2008-12-20 16:16 var
lrwxrwxrwx   1 root root    29 2008-12-20 19:54 vmlinuz -> boot/vmlinuz-2.6.27-9-generic
lrwxrwxrwx   1 root root    29 2008-12-20 15:54 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="28A89DDFA89DABB6" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="E09CC0B99CC08B8A" LABEL="BasWINDOWS" TYPE="ntfs" 
/dev/sda5: UUID="78E8C16FE8C12BE6" LABEL="BasDATA" TYPE="ntfs" 
/dev/sda6: UUID="059b2415-281d-4a02-9202-18e87a2a1644" TYPE="ext3" 
/dev/sda7: UUID="d12198fd-b0d6-4f8e-9a26-462614a03cb7" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe21d56ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    76511547    36718750    7  HPFS/NTFS
/dev/sda3        76517595   312576704   118029555    f  W95 Ext'd (LBA)
/dev/sda5       151091325   312576704    80742690    7  HPFS/NTFS
/dev/sda6        76517721   149725799    36604039+  83  Linux
/dev/sda7       149725863   151091324      682731   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3074048, size= 73437500, Id= 7, bootable
/dev/sda3 : start= 76517595, size=236059110, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=151091325, size=161485380, Id= 7
/dev/sda6 : start= 76517721, size= 73208079, Id=83
/dev/sda7 : start=149725863, size=  1365462, Id=82
ubuntu@ubuntu:~$ 

```

[by the way, Merry Christmas! Or if you don;t celebrate that holiday, happy-whatever-you-celebrate! I REALLY appreciate all the time you put into this. :) ]

---

### Post by caljohnsmith on 2008-12-24
> **Hydrothrax said:**
> 
[by the way, Merry Christmas! Or if you don;t celebrate that holiday, happy-whatever-you-celebrate! I REALLY appreciate all the time you put into this. :) ]
You're welcome, and Merry Christmas to you too! :) In order to fix your partition table problem, we're going to turn your sda5 NTFS partition into a primary partition, if that sounds OK with you. But before doing any partition changes, please be sure to back up all your important data. Once you've done that, download the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
Please post the output of the above command (it will produce warnings, so don't be alarmed), reboot your Live CD (it's important to reboot), and then do:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
sudo fdisk -lu
sudo sfdisk -sV
```
And please post the output of all the above commands. We can work from there. :)

---

### Post by Hydrothrax on 2008-12-24
```
ubuntu@ubuntu:~$ sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    191-    192-   1536000   27  Unknown
/dev/sda2   *    191+   4762-   4572-  36718750    7  HPFS/NTFS
/dev/sda3       4763   19456   14694  118029555    f  W95 Ext'd (LBA)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       9405   19456   10052   80742690    7  HPFS/NTFS
/dev/sda6       4763+   9319    4557-  36604039+  83  Linux
/dev/sda7       9320+   9404      85-    682731   82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1          2048   3074047    3072000  27  Unknown
/dev/sda2   *   3074048  76511547   73437500   7  HPFS/NTFS
/dev/sda3      76517595 151091324   74573730   f  W95 Ext'd (LBA)
/dev/sda4     151091325 312576704  161485380   7  HPFS/NTFS
/dev/sda5      76517721 149725799   73208079  83  Linux
/dev/sda6     149725863 151091324    1365462  82  Linux swap / Solaris
Warning: partition 1 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~$ 

```

Rebooting...hold on

EDIT: Part two

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe21d56ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    76511547    36718750    7  HPFS/NTFS
/dev/sda3        76517595   151091324    37286865    f  W95 Ext'd (LBA)
/dev/sda4       151091325   312576704    80742690    7  HPFS/NTFS
/dev/sda5        76517721   149725799    36604039+  83  Linux
/dev/sda6       149725863   151091324      682731   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo sfdisk -sV
/dev/sda: 156290904
Warning: partition 1 does not end at a cylinder boundary
total: 156290904 blocks
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2008-12-24
Great, go ahead and reboot, and let me know how far you get. :)

---

### Post by Hydrothrax on 2008-12-24
I can boot into Ubuntu! 8D

Grub still "sees" the other partitions, but that doesn't really bother me that much.

AND I can mount my Windows partition! I'm listening to music from it right now :)

---

### Post by caljohnsmith on 2008-12-24
That's great news, so it sounds like probably the last thing to do would be to clean up your Grub menu so it doesn't show the non-existent Ubuntu installations. How about running the script again on your new setup:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
As before, please copy/paste the contents of the "RESULTS.txt" file to your next post, and we can work from there. :)

---

### Post by Hydrothrax on 2008-12-25
```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #13 for its boot files.

sda1:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda10:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda11:
    File system:  swap

sda12:
    File system:  swap

sda13:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda14:
    File system:  swap

sda2:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3:
    File system:  Extended Partition

sda5:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0

sda6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda8:
    File system:  swap

sda9:
    File system:  swap


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe21d56ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    76511547    36718750    7  HPFS/NTFS
/dev/sda3        76517595   312576704   118029555    f  W95 Ext'd (LBA)
/dev/sda5       106735923   116503379     4883728+   7  HPFS/NTFS
/dev/sda6       116503443   125049959     4273258+  83  Linux
/dev/sda7       218210958   227367944     4578493+  83  Linux
/dev/sda8       227368008   229761629     1196811   82  Linux swap / Solaris
/dev/sda9       229761693   234677519     2457913+  82  Linux swap / Solaris
/dev/sda10      251160273   301154489    24997108+  83  Linux
/dev/sda11      301154553   304110449     1477948+  82  Linux swap / Solaris
/dev/sda12      304110513   312576704     4233096   82  Linux swap / Solaris
/dev/sda13       76517721   105370334    14426307   83  Linux
/dev/sda14      105370398   106735859      682731   82  Linux swap / Solaris

Partition table entries are not in disk order

Warning: partition 1 does not end at a cylinder boundary

/dev/sda1: UUID="28A89DDFA89DABB6" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="E09CC0B99CC08B8A" LABEL="BasWINDOWS" TYPE="ntfs" 
/dev/sda5: UUID="78E8C16FE8C12BE6" LABEL="BasDATA" TYPE="ntfs" 
/dev/sda6: UUID="3cf5f0f2-2931-4e31-b18a-fe48353e2618" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="7d0700e3-3833-42a0-85b5-a7fcfd0607b5" TYPE="swap" 
/dev/sda9: UUID="1953a983-6339-48b3-b88a-25c76a971d34" TYPE="swap" 
/dev/sda10: UUID="ac8a5550-96d0-4cbc-af90-fa81c821434a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="26c87295-fb50-46d6-a7e6-3aa1176d603f" TYPE="swap" 
/dev/sda12: UUID="3f1d249a-3528-4afb-a53d-7272d9c3633d" TYPE="swap" 
/dev/sda13: UUID="059b2415-281d-4a02-9202-18e87a2a1644" TYPE="ext3" 
/dev/sda14: UUID="22a16930-78f1-4ce1-a05d-6c598e6b1c30" TYPE="swap" 

sda10/boot/grub/menu.lst

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
# kopt=root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac8a5550-96d0-4cbc-af90-fa81c821434a

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
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ac8a5550-96d0-4cbc-af90-fa81c821434a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-12-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-12-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=51c344a9-4b88-4eb2-adce-2ae2b29bebe5 ro single 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda10/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1dde6d6e-3442-401a-af36-a864cff92a78 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda10/boot

total 12792
drwxr-xr-x  3 root root    4096 2008-11-26 11:32 .
drwxr-xr-x 21 root root    4096 2008-12-22 07:45 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-22 07:45 grub
-rw-r--r--  1 root root 8630005 2008-11-26 11:32 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic

sda10/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-22 07:45 .
drwxr-xr-x 3 root root   4096 2008-11-26 11:32 ..
-rw-r--r-- 1 root root    197 2008-11-29 11:10 default
-rw-r--r-- 1 root root     15 2008-11-29 11:10 device.map
-rw-r--r-- 1 root root   8108 2008-11-29 11:10 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-29 11:10 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-18 12:29 installed-version
-rw-r--r-- 1 root root   8712 2008-11-29 11:10 jfs_stage1_5
-rw-r--r-- 1 root root   6971 2008-11-26 11:29 menu.lst
-rw-r--r-- 1 root root   6971 2008-11-26 11:29 menu.lst~
-rw-r--r-- 1 root root   7352 2008-11-29 11:10 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-29 11:10 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-29 11:10 stage1
-rw-r--r-- 1 root root 121460 2008-11-29 11:10 stage2
-rw-r--r-- 1 root root   9556 2008-11-29 11:10 xfs_stage1_5

sda13/boot/grub/menu.lst

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
# kopt=root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=059b2415-281d-4a02-9202-18e87a2a1644

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
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, memtest86+ (on /dev/sda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda13/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda13
UUID=059b2415-281d-4a02-9202-18e87a2a1644 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda14
UUID=22a16930-78f1-4ce1-a05d-6c598e6b1c30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda13/boot

total 25508
drwxr-xr-x  3 root root    4096 2008-12-20 13:55 .
drwxr-xr-x 21 root root    4096 2008-12-20 14:20 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-20 13:54 grub
-rw-r--r--  1 root root 8660919 2008-12-20 13:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8661204 2008-12-20 13:55 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

sda13/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-20 13:54 .
drwxr-xr-x 3 root root   4096 2008-12-20 13:55 ..
-rw-r--r-- 1 root root    197 2008-12-20 10:20 default
-rw-r--r-- 1 root root     15 2008-12-20 10:20 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 10:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 10:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 10:20 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 10:20 jfs_stage1_5
-rw-r--r-- 1 root root   7857 2008-12-20 13:54 menu.lst
-rw-r--r-- 1 root root   7773 2008-12-20 13:54 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-20 10:20 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 10:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 10:20 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 10:20 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 10:20 xfs_stage1_5

sda6/boot/grub/menu.lst

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
# kopt=root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3cf5f0f2-2931-4e31-b18a-fe48353e2618

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
uuid		3cf5f0f2-2931-4e31-b18a-fe48353e2618
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3cf5f0f2-2931-4e31-b18a-fe48353e2618
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3cf5f0f2-2931-4e31-b18a-fe48353e2618
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=76e7fce5-0f30-476b-a655-4b339c371764 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda6/boot

total 12804
drwxr-xr-x  3 root root    4096 2008-11-29 11:50 .
drwxr-xr-x 20 root root    4096 2008-12-22 10:26 ..
-rw-r--r--  1 root root  503560 2008-10-24 02:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 02:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-06 06:43 grub
-rw-r--r--  1 root root 8641483 2008-11-29 11:49 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 02:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 02:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 02:55 vmlinuz-2.6.27-7-generic

sda6/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-06 06:43 .
drwxr-xr-x 3 root root   4096 2008-11-29 11:50 ..
-rw-r--r-- 1 root root    197 2008-12-06 06:43 default
-rw-r--r-- 1 root root     45 2008-12-06 06:43 device.map
-rw-r--r-- 1 root root   8108 2008-12-06 06:43 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-06 06:43 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-29 11:50 installed-version
-rw-r--r-- 1 root root   8712 2008-12-06 06:43 jfs_stage1_5
-rw-r--r-- 1 root root   5539 2008-11-29 11:50 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-06 06:43 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-06 06:43 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-06 06:43 stage1
-rw-r--r-- 1 root root 121460 2008-12-06 06:43 stage2
-rw-r--r-- 1 root root   9556 2008-12-06 06:43 xfs_stage1_5

sda7/boot/grub/menu.lst

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
# kopt=root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3

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
uuid		e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, memtest86+ (on /dev/sda8)
root		(hd0,7)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda7/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda12
UUID=dc14f144-c290-472c-877b-1bd8bc26b6a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda7/boot

total 12804
drwxr-xr-x  3 root root    4096 2008-12-07 04:54 .
drwxr-xr-x 20 root root    4096 2008-12-22 09:50 ..
-rw-r--r--  1 root root  503560 2008-10-24 02:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 02:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-07 04:55 grub
-rw-r--r--  1 root root 8642124 2008-12-07 04:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 02:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 02:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 02:55 vmlinuz-2.6.27-7-generic

sda7/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-07 04:55 .
drwxr-xr-x 3 root root   4096 2008-12-07 04:54 ..
-rw-r--r-- 1 root root    197 2008-12-07 04:54 default
-rw-r--r-- 1 root root     15 2008-12-07 04:54 device.map
-rw-r--r-- 1 root root   8108 2008-12-07 04:54 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-07 04:54 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-07 04:55 installed-version
-rw-r--r-- 1 root root   8712 2008-12-07 04:54 jfs_stage1_5
-rw-r--r-- 1 root root   6451 2008-12-07 04:55 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-07 04:54 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-07 04:54 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-07 04:54 stage1
-rw-r--r-- 1 root root 121460 2008-12-07 04:55 stage2
-rw-r--r-- 1 root root   9556 2008-12-07 04:54 xfs_stage1_5

StdErr Messages 

```

Funny that it says "unclean shutdown" for sda1. It has no OS [that I know of] since that is my system volume for my TOSHIBA laptop.... o well XD

---

### Post by caljohnsmith on 2008-12-25
I think I see what happened, and I see it was my mistake; you posted the "RESULTS.txt" file like I asked, but it was from your previous results before you did all the partition changes (it's the same as your post #3 results). When you run the script more than once, it adds numbering to each RESULTS.txt file it creates so previous results files are not overwritten; so the new results file might be "RESULTS1.txt", "RESULTS2.txt", etc. Or you could just delete all RESULTS.txt files on your desktop and then run the script again. But bottom line, please post the latest results file. :)

---

### Post by Hydrothrax on 2008-12-25
Aha! So this one? 
```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #5 for its boot files.

sda1:
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda2 starts at sector 3074048.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sda3:
    File system:  Extended Partition

sda4:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda4 starts at sector 151091325.
    Operating System: XP
    Boot files/directories present: 

sda5:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6:
    File system:  swap


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe21d56ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    76511547    36718750    7  HPFS/NTFS
/dev/sda3        76517595   151091324    37286865    f  W95 Ext'd (LBA)
/dev/sda4       151091325   312576704    80742690    7  HPFS/NTFS
/dev/sda5        76517721   149725799    36604039+  83  Linux
/dev/sda6       149725863   151091324      682731   82  Linux swap / Solaris

Warning: partition 1 does not end at a cylinder boundary

/dev/sda1: UUID="28A89DDFA89DABB6" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="E09CC0B99CC08B8A" LABEL="BasWINDOWS" TYPE="ntfs" 
/dev/sda4: UUID="78E8C16FE8C12BE6" LABEL="BasDATA" TYPE="ntfs" 
/dev/sda5: UUID="059b2415-281d-4a02-9202-18e87a2a1644" TYPE="ext3" 
/dev/sda6: UUID="d12198fd-b0d6-4f8e-9a26-462614a03cb7" TYPE="swap" 

sda2/boot.ini

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.1

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.1="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


sda5/boot/grub/menu.lst

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
# kopt=root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=059b2415-281d-4a02-9202-18e87a2a1644

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
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=059b2415-281d-4a02-9202-18e87a2a1644 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		059b2415-281d-4a02-9202-18e87a2a1644
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, memtest86+ (on /dev/sda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda5/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda13
UUID=059b2415-281d-4a02-9202-18e87a2a1644 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda14
UUID=22a16930-78f1-4ce1-a05d-6c598e6b1c30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda5/boot

total 25508
drwxr-xr-x  3 root root    4096 2008-12-20 13:55 .
drwxr-xr-x 21 root root    4096 2008-12-20 14:20 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-20 13:54 grub
-rw-r--r--  1 root root 8660919 2008-12-20 13:54 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8661204 2008-12-20 13:55 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

sda5/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-20 13:54 .
drwxr-xr-x 3 root root   4096 2008-12-20 13:55 ..
-rw-r--r-- 1 root root    197 2008-12-20 10:20 default
-rw-r--r-- 1 root root     15 2008-12-20 10:20 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 10:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 10:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 10:20 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 10:20 jfs_stage1_5
-rw-r--r-- 1 root root   7857 2008-12-20 13:54 menu.lst
-rw-r--r-- 1 root root   7773 2008-12-20 13:54 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-20 10:20 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 10:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 10:20 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 10:20 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 10:20 xfs_stage1_5

StdErr Messages 

```

BTW would getting rid of Windows on sda4 mess anything up? That partition was later to be used as my data partition, so I can access my stuff from both operating systems.

---

### Post by caljohnsmith on 2008-12-25
[QUOTE=Hydrothrax]BTW would getting rid of Windows on sda4 mess anything up? That partition was later to be used as my data partition, so I can access my stuff from both operating systems.[/QUOTE]
You should be just fine if you want to get rid of Windows on sda4; I would recommend just reformatting the partition rather than actually deleting the partition, but either way shouldn't break your booting process.

But about your Grub menu issue, while you are in Ubuntu, how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And then delete everything in your menu.lst that is highlighted in red below:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

[COLOR="Red"]
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ac8a5550-96d0-4cbc-af90-fa81c821434a ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 8.10, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot
[/COLOR]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


[COLOR="Red"]# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3cf5f0f2-2931-4e31-b18a-fe48353e2618 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e54c5fd2-3e1b-45f6-9c0c-727d9522c6a3 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, memtest86+ (on /dev/sda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot
[/COLOR]
```
And then you should be all set. Let me know how it goes or if you run into problems. :)

---

### Post by Hydrothrax on 2008-12-25
IT WORKED. PERFECTLY.

God I love Linux.... now if only Windows CDs were as easy to get as Linux CDs... :)

---

