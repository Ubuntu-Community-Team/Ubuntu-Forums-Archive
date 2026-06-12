---
title: "[SOLVED] grub error 21"
date: 2008-12-22
forum: Hardware
---

### Post by inxygnuu on 2008-12-22
hello, from a live cd, I have a problem. GRUB! I wanted to install Ubuntu on a flash drive, so that I would have a backup if i needed one, but all it gave me was an unbootable flash drive, and GRUB error 21. Does anyone know how to fix this? I am going to maybe, wipe my drive in a month, but I really need my system for 2 school projects. When I try to boot into my usb, it tells me "invalid or damaged bootable partition", and when i boot into GRUB, it says "GRUB loading, please wait... Grub loading stage 1.5. grub error 21" I am on a live cd right now, so I have access to all of my files, but I need certain programs to do my projects.

Help would be greatly appreciated,
3v4n

---

### Post by inxygnuu on 2008-12-22
ok, I got my system booted, but I always have to have a usb flash drive in. any recommendations on how to fix this?

---

### Post by caljohnsmith on 2008-12-22
Sounds like you might have Grub installed to the MBR (Master Boot Record) of your internal drive while Ubuntu is actually on your flash drive. Can you set your BIOS to boot the flash drive? That would be most ideal for your situation, because then I can help you install Grub to your flash drive and make it bootable. That way your drives can be independent and you won't need to plug in your flash drive to boot Windows on your internal drive.

In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by inxygnuu on 2008-12-22
Thanks for helping again caljohnsmith:)!

Yeah, I know that happened, and here is what is happening: My when I reinstalled Ubuntu onto a usb, it reinstalled Grub on my MBR. And then it put the boot files on my usb, so when my usb flash drive goes to boot up, it looks for the files on the computer. problem is, I want them completely independent, because the usb is 100% backup for now. (just in case something like this happens:))

So can you explain any steps i need to take, because i am in vista right now, with a lot of things running, and I need them to be running for a while.

---

### Post by inxygnuu on 2008-12-22
Here are the results:

Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #1 for its boot files.
No known boot loader is installed in the MBR of /dev/sdb

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
    File system:  ntfs
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 sda6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 sda6 ntfs-3g force 0 0

sda7:
    File system:  swap

sda8:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ddd1ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62363647    31180800    7  HPFS/NTFS
/dev/sda3        62364330   390716864   164176267+   5  Extended
/dev/sda5   *    68517288   244332584    87907648+   7  HPFS/NTFS
/dev/sda6       310022144   390715391    40346624    7  HPFS/NTFS
/dev/sda7        62364456    68517224     3076384+  82  Linux swap / Solaris
/dev/sda8       244332648   310006304    32836828+  83  Linux

Partition table entries are not in disk order

Warning: partition 1 does not end at a cylinder boundary


Disk /dev/sdb: 4063 MB, 4063232000 bytes
16 heads, 32 sectors/track, 15500 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ec681

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7935487     3967728   83  Linux

Warning: partition 1 does not end at a cylinder boundary
/dev/sdb: OK

/dev/sda1: UUID="924EB29B4EB27795" LABEL="Evan" TYPE="ntfs" 
/dev/sda5: UUID="0CBC28F9BC28DF48" LABEL="Vista" TYPE="ntfs" 
/dev/sda6: UUID="F63638343637F469" LABEL="Backup" TYPE="ntfs" 
/dev/sda7: UUID="1d498d75-062a-4edd-abda-675ed57606d4" TYPE="swap" 
/dev/sda8: UUID="1869fedd-4125-4bbc-94ff-65c782c2f77c" TYPE="ext3" 
/dev/sdb1: UUID="0fca5413-a523-4573-b8ea-b38ee9b7ce9c" SEC_TYPE="ext2" TYPE="ext3" 

sda8/boot/grub/menu.lst

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
# kopt=root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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
# defoptions=quiet splash vga=792

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
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows
rootnoverify (hd0,0)
chainloader +1

sda8/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=1d498d75-062a-4edd-abda-675ed57606d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda8/boot

total 35000
drwxr-xr-x  3 root root    4096 2008-11-28 10:46 .
drwxr-xr-x 21 root root    4096 2008-11-28 10:40 ..
-rw-r--r--  1 root root  422667 2008-06-18 14:11 abi-2.6.24-19-generic
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   80049 2008-06-18 14:11 config-2.6.24-19-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-14 19:52 grub
-rw-r--r--  1 root root 8265639 2008-11-26 19:46 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 8120885 2008-11-26 19:45 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8121863 2008-11-28 10:46 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root  905146 2008-06-18 14:11 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920472 2008-06-18 14:11 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

sda8/boot/grub

total 240
drwxr-xr-x 3 root root   4096 2008-12-14 19:52 .
drwxr-xr-x 3 root root   4096 2008-11-28 10:46 ..
-rw-r--r-- 1 root root    197 2008-11-26 12:31 default
-rw-r--r-- 1 root root     15 2008-11-26 12:31 device.map
-rw-r--r-- 1 root root   8056 2008-11-26 12:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-26 12:31 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-26 12:31 installed-version
-rw-r--r-- 1 root root   8608 2008-11-26 12:31 jfs_stage1_5
-rw-r--r-- 1 root root   4679 2008-12-14 19:52 menu.lst
-rw-r--r-- 1 root root   4903 2008-12-14 16:17 menu.lst~
-rw-r--r-- 1 root root   4620 2008-11-26 19:33 menu.lst-backup
-rw-r--r-- 1 root root   4624 2008-11-26 18:59 menu.lst.backup
-rw-r--r-- 1 root root   4624 2008-11-26 18:49 menu.lst_original
-rw-r--r-- 1 root root   7324 2008-11-26 12:31 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-11-26 12:31 reiserfs_stage1_5
drwxrwxr-x 2 root evan   4096 2008-11-26 18:50 splashimages
-rw-r--r-- 1 root root    512 2008-11-26 12:31 stage1
-rw-r--r-- 1 root root 108356 2008-11-26 12:31 stage2
-rw-r--r-- 1 root root   9276 2008-11-26 12:31 xfs_stage1_5

sdb1/boot/grub/menu.lst

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
# kopt=root=UUID=0fca5413-a523-4573-b8ea-b38ee9b7ce9c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0fca5413-a523-4573-b8ea-b38ee9b7ce9c

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
uuid		0fca5413-a523-4573-b8ea-b38ee9b7ce9c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0fca5413-a523-4573-b8ea-b38ee9b7ce9c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0fca5413-a523-4573-b8ea-b38ee9b7ce9c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0fca5413-a523-4573-b8ea-b38ee9b7ce9c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0fca5413-a523-4573-b8ea-b38ee9b7ce9c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.24-19-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, memtest86+ (on /dev/sda8)
root		(hd0,7)
kernel		/boot/memtest86+.bin  
savedefault
boot


sdb1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0fca5413-a523-4573-b8ea-b38ee9b7ce9c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=1d498d75-062a-4edd-abda-675ed57606d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sdb1/boot

total 12812
drwxr-xr-x  3 root root    4096 2008-12-21 23:17 .
drwxr-xr-x 20 root root    4096 2008-12-21 23:17 ..
-rw-r--r--  1 root root  503560 2008-10-24 03:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 03:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-21 23:18 grub
-rw-r--r--  1 root root 8647043 2008-12-21 23:17 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 03:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 03:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 03:55 vmlinuz-2.6.27-7-generic

sdb1/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-21 23:18 .
drwxr-xr-x 3 root root   4096 2008-12-21 23:17 ..
-rw-r--r-- 1 root root    197 2008-12-21 23:17 default
-rw-r--r-- 1 root root     30 2008-12-21 23:17 device.map
-rw-r--r-- 1 root root   8108 2008-12-21 23:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-21 23:17 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-21 23:17 installed-version
-rw-r--r-- 1 root root   8712 2008-12-21 23:17 jfs_stage1_5
-rw-r--r-- 1 root root   6243 2008-12-21 23:18 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-21 23:17 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-21 23:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-21 23:17 stage1
-rw-r--r-- 1 root root 121460 2008-12-21 23:17 stage2
-rw-r--r-- 1 root root   9556 2008-12-21 23:17 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sdb

00000000  fa be 00 7c bf 00 7a b9  00 01 fc 0e 1f 0e 07 f3  |...|..z.........|
00000010  a5 ea 16 7a 00 00 bb be  7b 33 c9 80 3f 80 75 06  |...z....{3..?.u.|
00000020  fe c5 8b f3 eb 07 80 3f  00 75 02 fe c1 83 c3 10  |.......?.u......|
00000030  81 fb fe 7b 72 e5 83 f9  04 74 0b 81 f9 03 01 74  |...{r....t.....t|
00000040  0a bb a5 7a eb 2c bb 87  7a eb 27 8b 4c 02 8b 14  |...z.,..z.'.L...|
00000050  b8 01 02 bb 00 7c cd 13  73 05 bb bc 7a eb 13 2e  |.....|..s...z...|
00000060  a1 fe 7d 3d 55 aa 74 05  bb bc 7a eb 05 ea 00 7c  |..}=U.t...z....||
00000070  00 00 2e 8a 07 3c 00 74  0c 53 bb 07 00 b4 0e cd  |.....<.t.S......|
00000080  10 5b 43 eb ed eb fe 4e  6f 20 62 6f 6f 74 61 62  |.[C....No bootab|
00000090  6c 65 20 70 61 72 74 69  74 6f 6e 20 69 6e 20 74  |le partiton in t|
000000a0  61 62 6c 65 00 49 6e 76  61 6c 69 64 20 50 61 72  |able.Invalid Par|
000000b0  74 69 74 6f 6e 20 74 61  62 6c 65 00 49 6e 76 61  |titon table.Inva|
000000c0  6c 69 64 20 6f 72 20 64  61 6d 61 67 65 64 20 42  |lid or damaged B|
000000d0  6f 6f 74 61 62 6c 65 20  70 61 72 74 69 74 69 6f  |ootable partitio|
000000e0  6e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |n...............|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  81 c6 0e 00 00 00 80 01  |................|
000001c0  01 00 83 0f e0 ff 20 00  00 00 e0 15 79 00 00 00  |...... .....y...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by inxygnuu on 2008-12-22
oops, sorry my vista never shuts down correctly, so I had to do a hard-boot. I will fix that in a while. I cant mount the usb in Ubuntu either. Error: "Error org.freedesktop.Hal.Device.UnknownError."

---

### Post by caljohnsmith on 2008-12-22
OK, that's great, thanks for posting the output of the script; that greatly clarifies your setup. How about doing:
```
sudo grub
grub> root (hd0,7)
grub> setup (hd0)
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Please post the output of all the above commands, reboot, set your BIOS to boot the flash drive, and you should be able to boot into Ubuntu on your flash drive OK. Also, if you set your BIOS to boot your Windows sda drive, you should get back your other Grub menu where you can boot Windows or Ubuntu on the sda drive. How about giving that a shot and let me know how it goes. :)

---

### Post by inxygnuu on 2008-12-22
Oh, i am sorry, i am in Ubuntu right now. All i had to was put in the flash drive during the boot, and it boots!:) I need my flash drive and GRUB to be completely independent from each other. I am going to use the flash drive as a backup, just in case something like this happens. Thanks for the help!

---

### Post by inxygnuu on 2008-12-22
ok, here are the results in order:

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,7)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> root (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

---

### Post by inxygnuu on 2008-12-22
Thanks! (again) suddenly, it works! Don't know why, but it works!:):popcorn::KS:guitar::P Now, tomorrow i will try to see if the usb is bootable.

---

