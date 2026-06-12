---
title: "SATA/IDE/grub help!"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by andy.t on 2008-12-23
Hi,

Noob issue...

Configuration:

XP Pro on IDE drive.
Installed ubuntu 8.10 on empty (sata) drive, via the live cd.
At an "advanced" tab (noob mistake?), I selected "load boot loader" and chose the same drive as the XP installation. I'd previously installed ubuntu on the SATA drive, but there was no boot loader on re-boot and hence I couldn't boot into ubuntu.

Installation went fine, but now the computer won't boot into either operating systems! all I get is "GRUB" and a flashing cursor.

Certainly ubuntu is there somewhere, and I'd assume XP is still there - but neither will load.

Help! (from a second pc...)

Andy

---

### Post by andy.t on 2008-12-23
Following on...

Didn't mention that GRUB appears to be frozen, I can't enter anything at the flashing cursor.

I found [this ]("http://ubuntuforums.org/showthread.php?t=1019451&highlight=grub")message, followed the fist reply. I found that my /boot/grub/stage1 was on (hd0,0) (does that make sense?), so at a grub command line I typed root "(hd0,0)" then I typed "setup (hd0). According to the other post, this should have fixed grub. But on re-boot I got exactly the same thing.

So then I tried the second reply, and tried to install a windows equivalent MBR from the live cd, but that didn't work either!

My XP Pro installation is on sdc, by the way.

Still no operating system! help...

tia! Andy

---

### Post by andy.t on 2008-12-23
Progress, sort of...

ok, managed to get grub working - by following the instructions in the previous post I linked to (after realising that I needed to install grub to another hard drive - not hd0).

So, I now have a fully working ubuntu 8.10 on my sata drive, and I'm trying to access or recover my XP Pro installation. But is it still there?...

From within ubuntu, I've managed to browse my computer. I can see "filesystem" (presumably the ubuntu sata drive), I can see another IDE drive I have and I can see my cd drive - but I can't see the ide drive where XP Pro was.

Have I deleted my XP Pro installation? to reiterate, when installing ubuntu to the sata drive, I asked the bootloader to be installed on my XP Pro drive...

Ta! Andy

---

### Post by caljohnsmith on 2008-12-23
It sounds like you may have accidentally installed Grub to the boot sector of your Windows partition, which unfortunately would make Windows unbootable until you fix it. In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by logos34 on 2008-12-23
delete

---

### Post by andy.t on 2008-12-23
Thanks, it's long - but here it is:


Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on boot drive #1 in partition #1 for its boot files.
Grub is installed in the MBR of /dev/sdc and looks on boot drive #1 in partition #1 for its boot files.

sda1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2:
    File system:  Extended Partition

sda5:
    File system:  swap

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63.
    Operating System: 
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sdc1:
    File system:  
    Mounting failed:  
mount: you must specify the filesystem type


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52e1e07e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   619080839   309540388+  83  Linux
/dev/sda2       619080840   625137344     3028252+   5  Extended
/dev/sda5       619080903   625137344     3028221   82  Linux swap / Solaris

/dev/sdc1: unknown volume type
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK


Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f7d2f7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   160810649    80405293+   7  HPFS/NTFS

/dev/sdc1: unknown volume type
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK
/dev/sdb: OK


Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf75804ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   280575224   140287581    7  HPFS/NTFS

/dev/sdc1: unknown volume type
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK
/dev/sdb: OK
/dev/sdc: OK

/dev/sda1: UUID="f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82" TYPE="ext3" 
/dev/sda5: UUID="9695055a-295e-4735-bae3-d848d25bbb12" TYPE="swap" 
/dev/sdb1: UUID="A4A0C129A0C10332" LABEL="large data" TYPE="ntfs" 

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
# kopt=root=UUID=f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82

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
uuid		f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


sda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f7c47ed6-ad7a-4b65-b8e9-2f0826bf8b82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9695055a-295e-4735-bae3-d848d25bbb12 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda1/boot

total 23792
drwxr-xr-x  3 root root    4096 2008-12-24 00:36 .
drwxr-xr-x 20 root root    4096 2008-12-24 00:34 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-24 00:34 grub
-rw-r--r--  1 root root 8196088 2008-12-24 00:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8196704 2008-12-24 00:36 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

sda1/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-24 00:34 .
drwxr-xr-x 3 root root   4096 2008-12-24 00:36 ..
-rw-r--r-- 1 root root    197 2008-12-23 21:53 default
-rw-r--r-- 1 root root     45 2008-12-23 21:53 device.map
-rw-r--r-- 1 root root   8108 2008-12-23 21:53 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-23 21:53 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-23 21:53 installed-version
-rw-r--r-- 1 root root   8712 2008-12-23 21:53 jfs_stage1_5
-rw-r--r-- 1 root root   5329 2008-12-24 00:34 menu.lst
-rw-r--r-- 1 root root   5245 2008-12-24 00:34 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-23 21:53 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-23 21:53 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-23 21:53 stage1
-rw-r--r-- 1 root root 121460 2008-12-23 21:53 stage2
-rw-r--r-- 1 root root   9556 2008-12-23 21:53 xfs_stage1_5

sdb1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


StdErr Messages 

/dev/sdc1: unknown volume type

---

### Post by andy.t on 2008-12-23
ps. my XP disk is the unmountable sdc1.

Ta!

Andy

---

### Post by caljohnsmith on 2008-12-23
How about booting your Windows Install CD, go to the "recovery console" and run:
```
fixboot
```
After that, try mounting the sdc1 partition in Ubuntu and let me know if it works.

---

