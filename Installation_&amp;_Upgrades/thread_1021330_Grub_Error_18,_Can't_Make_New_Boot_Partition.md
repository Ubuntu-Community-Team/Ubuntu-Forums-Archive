---
title: "Grub Error 18, Can't Make New Boot Partition"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by matt11601 on 2008-12-25
I've been struggling with this problem and could use some help.

**Background** 
I'm running Ubuntu Server on an old machine (PII, 300 mhz). Everything has been working well until last week. Last week, I updated the system using "apt-get update" and then "apt-get upgrade". I rebooted the system (reboot -h now) and now get the Grub 18 Error. If I go to the grub menu and select ubuntu, I still get Grub 18. The only thing that does work from the Grub menu is MemTest.

After researching this issue, I believe my problem is that the kernel is now located outside of the BIOS HD limit as described by Herman [here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition") and [here]("http://ubuntuforums.org/showthread.php?t=582855").

If I understand those links correctly, the recommendation is creating a new /boot partition at the very beginning of the drive. Then take your existing boot folder, transfer it to this newly created boot partition and then edit Grub accordingly. This is what I'm trying to do right now.

**Problem**
Gparted crashes when I try to create unallocated space at the very beginning of the disk.

Here's what GParted looks like:

++++++++++++++++++++++++++++++++++
/dev/hda1 ext3         ~230 GB  Used ~176 GB    Unused ~55 GB
/dev/hda2 extended     ~352 MB
---/dev/hda5 linux swap ~352 MB 
++++++++++++++++++++++++++++++++++

All my data is on hda1 including ubuntu server, home movies, pictures, etc, etc etc.

**I Did This**
-Grabbed the latest GParted Live CD and burned it 
-Ran GParted
-Removed the "boot" flag from hda1
-Shrank hda1 and told GParted to put the new unallocated space in front of hda1 (thus new space at the very beginning of drive)

When I click apply, GParted goes to work ("Move /dev/hda1 to the right and shrink it from ~231 GB to ~230 GB"). But then GParted suddenly disappears in a few minutes. When I re-launch GParted, my partition scheme is back to its original state with no changes made.

Can someone please help? I suspect I'm overlooking something but I'm completely lost now.

Thank you very much.

-Matt

---

### Post by caljohnsmith on 2008-12-25
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your partitioning problem might be.

---

### Post by matt11601 on 2008-12-25
Here's the contents of that file. I also attached it.

One important thing. hda3 is a new partition I just created with the gparted live cd. It was going to be the new /boot partition. I never deleted it so it's still on the system. 

> 
Grub is installed in the MBR of /dev/hda and looks on the same drive in partition #1 for its boot files.
No boot loader is installed in the MBR of /dev/hdc

hda1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.04.1 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

hda2:
    File system:  Extended Partition

hda3:
    File system:  ext2
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

hda5:
    File system:  swap


Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   484279487   242139712+  83  Linux
/dev/hda2       487669140   488392064      361462+   5  Extended
/dev/hda3       487203255   487669139      232942+  83  Linux
/dev/hda5       487669203   488392064      361431   82  Linux swap / Solaris

Partition table entries are not in disk order

Warning: partition 1 does not end at a cylinder boundary

Note: sector size is 2048 (not 512)

Disk /dev/hdc: 732 MB, 732336128 bytes
255 heads, 63 sectors/track, 22 cylinders, total 357586 sectors
Units = sectors of 1 * 2048 = 2048 bytes


Warning: partition 1 does not end at a cylinder boundary

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/hdc: unrecognized partition table type

sfdisk: no partition table present.

/dev/hda1: UUID="4ce58e3a-d384-46a9-b1c3-bed9f4177e4d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="5ac0e618-6fb9-4de9-9b81-be4acfa6175c" TYPE="ext2" 
/dev/hda5: UUID="a121315a-a70d-4848-bea6-6387fd3472f8" TYPE="swap" 
/dev/evms/hda1: UUID="4ce58e3a-d384-46a9-b1c3-bed9f4177e4d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/hda3: UUID="5ac0e618-6fb9-4de9-9b81-be4acfa6175c" TYPE="ext2" 
/dev/evms/hda5: UUID="a121315a-a70d-4848-bea6-6387fd3472f8" TYPE="swap" 

unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

hda1/boot/grub/menu.lst

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
# kopt=root=UUID=4ce58e3a-d384-46a9-b1c3-bed9f4177e4d ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=4ce58e3a-d384-46a9-b1c3-bed9f4177e4d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-server
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=4ce58e3a-d384-46a9-b1c3-bed9f4177e4d ro single
initrd		/boot/initrd.img-2.6.24-16-server

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

hda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4ce58e3a-d384-46a9-b1c3-bed9f4177e4d /               ext3    relatime,acl,errors=remount-ro 0       1
# /dev/sda5
UUID=a121315a-a70d-4848-bea6-6387fd3472f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

hda1/boot

total 17880
drwxr-xr-x  3 root root    4096 2008-12-16 22:47 .
drwxr-xr-x 22 root root    4096 2008-09-20 14:09 ..
-rw-r--r--  1 root root  426444 2008-04-10 16:55 abi-2.6.24-16-server
-rw-r--r--  1 root root   80203 2008-04-10 16:55 config-2.6.24-16-server
drwxr-xr-x  2 root root    4096 2008-07-05 19:21 grub
-rw-r--r--  1 root root 7352144 2008-12-16 22:47 initrd.img-2.6.24-16-server
-rw-r--r--  1 root root 7353409 2008-09-18 10:55 initrd.img-2.6.24-16-server.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  933296 2008-04-10 16:55 System.map-2.6.24-16-server
-rw-r--r--  1 root root 1987288 2008-04-10 16:55 vmlinuz-2.6.24-16-server

hda1/boot/grub

total 204
drwxr-xr-x 2 root root   4096 2008-07-05 19:21 .
drwxr-xr-x 3 root root   4096 2008-12-16 22:47 ..
-rw-r--r-- 1 root root    197 2008-07-05 19:21 default
-rw-r--r-- 1 root root     15 2008-07-05 19:21 device.map
-rw-r--r-- 1 root root   8056 2008-07-05 19:21 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-07-05 19:21 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-07-05 19:21 installed-version
-rw-r--r-- 1 root root   8608 2008-07-05 19:21 jfs_stage1_5
-rw-r--r-- 1 root root   4259 2008-07-05 19:21 menu.lst
-rw-r--r-- 1 root root   7324 2008-07-05 19:21 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-07-05 19:21 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-07-05 19:21 stage1
-rw-r--r-- 1 root root 108356 2008-07-05 19:21 stage2
-rw-r--r-- 1 root root   9276 2008-07-05 19:21 xfs_stage1_5

StdErr Messages 

Disk /dev/hdc doesn't contain a valid partition table


---

### Post by caljohnsmith on 2008-12-25
Nothing looks unusual about your setup that I can see (at least based on the results you posted), so I'm not sure why gparted would crash on you. You mentioned you are using the latest version of gparted, so how about trying a slightly earlier version and see if you get any further. For instance, you could download the Gutsy or Hardy Live CD and use the gparted version that comes with it to see if it makes any difference.

---

### Post by matt11601 on 2008-12-27
caljohnsmith you were 100% right, it was GParted. The latest stable release of GParted might have a bug because I used an older version and everything is working fine now.

I was able to move my partition, create a new boot (thanks to Herman's wonderful page) and get my media server back online.

It's the holidays and getting this box back online was crucial for everyone. Thank you very much caljohnsmith.

-Matt

---

### Post by caljohnsmith on 2008-12-27
You're certainly welcome, and I'm glad that it didn't turn out to be a more serious problem; cheers and hope you don't run into any other major problems with your media server setup. :)

---

