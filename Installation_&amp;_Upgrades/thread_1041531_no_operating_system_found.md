---
title: "no operating system found"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by kainalu on 2009-01-16
Im trying to install xubuntu to an older hp desktop. upon rebooting off the cd after install, I get a message no operating system found. the problem seems to lie in the way grub is installed but im not sure. puppy linux will install and work if the grub is placed on sda1, but will not work if placed in MBR. is there a way to make grub go to sda1 for xubuntu. If it already does this, why is it not booting? thanks guys!


--Kainalu

---

### Post by cariboo on 2009-01-16
You can boot from the Livecd and reinstall grub, by following the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351").

Jim

---

### Post by kainalu on 2009-01-17
the boot loader cant be on the MBR or this particular system will not boot, it needs to be installed to the first partiton

--Kainalu

---

### Post by caljohnsmith on 2009-01-17
Kainalu, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by kainalu on 2009-01-17
here it is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36423641

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    38780909    19390423+  83  Linux
/dev/sda2        38780910    39873329      546210    5  Extended
/dev/sda5        38780973    39873329      546178+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="ce5ef947-e5b8-454f-a91c-500b54ef8eb4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="d35a90b9-be86-422d-ae03-00ad6fff89e1" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

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
# kopt=root=UUID=ce5ef947-e5b8-454f-a91c-500b54ef8eb4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ce5ef947-e5b8-454f-a91c-500b54ef8eb4

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
uuid		ce5ef947-e5b8-454f-a91c-500b54ef8eb4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ce5ef947-e5b8-454f-a91c-500b54ef8eb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ce5ef947-e5b8-454f-a91c-500b54ef8eb4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ce5ef947-e5b8-454f-a91c-500b54ef8eb4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ce5ef947-e5b8-454f-a91c-500b54ef8eb4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ce5ef947-e5b8-454f-a91c-500b54ef8eb4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d35a90b9-be86-422d-ae03-00ad6fff89e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11956
drwxr-xr-x  3 root root    4096 2009-01-17 00:15 .
drwxr-xr-x 20 root root    4096 2009-01-16 22:53 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-17 00:16 grub
-rw-r--r--  1 root root 8184783 2009-01-17 00:14 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-17 00:16 .
drwxr-xr-x 3 root root   4096 2009-01-17 00:15 ..
-rw-r--r-- 1 root root    197 2009-01-17 00:15 default
-rw-r--r-- 1 root root     15 2009-01-17 00:15 device.map
-rw-r--r-- 1 root root   8108 2009-01-17 00:15 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-17 00:15 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-17 00:15 installed-version
-rw-r--r-- 1 root root   8712 2009-01-17 00:15 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2009-01-17 00:16 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-17 00:15 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-17 00:15 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-17 00:15 stage1
-rw-r--r-- 1 root root 121460 2009-01-17 00:15 stage2
-rw-r--r-- 1 root root   9556 2009-01-17 00:15 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-17
First, can you check that your sda drive is right after the CD/DVD drive in your BIOS boot order? It looks like Grub is installed correctly to your sda drive, and also one partition is marked as bootable; so I'm not sure why you would get a "no operating system found" error. It sounds like previously you were able to get Puppy Linux to work because you kept the HP MBR (Master Boot Record), and instead installed Grub to the Puppy partition. You could do the same for Xubuntu, but you would need to somehow restore the HP MBR. Do you have any Install CDs that came with your HP computer? If so, are they all OEM, or do they also offer a command line you can use when you boot them?

---

### Post by kainalu on 2009-01-17
i did not keep the hp boot mbr. I gparted the disk and created the msdos disk label. installed xubuntu. this failed with no os found. upon this error, i re-formatted the drive including disk label again, installed puppy to mbr. when this failed, i installed puppy to disk boot record. this works. I reinstalled xubuntu and it failed again.


is there a list of commands to just make it boot off the first boot partition instead of the mbr like puppy does?

---

### Post by caljohnsmith on 2009-01-17
> **kainalu said:**
> 
is there a list of commands to just make it boot off the first boot partition instead of the mbr like puppy does?
Actually, you always have to boot from the MBR when you boot the HDD, is just that when you installed Puppy's boot loader to the boot sector of its own partition, you probably had a Windows type MBR at the time that boots whichever partition is marked bootable. I'm not sure if that will make any difference with Ubuntu, but it wouldn't hurt to try:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
sudo grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
```
And please post the output of all the above commands before doing "quit". Then reboot, and let me know exactly what happens.

---

### Post by kainalu on 2009-01-17
sudo apt-get install lilo
Bus error (core dumped). 79%

---

### Post by caljohnsmith on 2009-01-17
If you got a bus error, it looks like you may have more problems than just with booting Ubuntu. How about booting the Live CD again, but at the main menu choose the "check memory" type option that allows you to run memtest86+ in order to check your RAM. Let me know if that turns up anything after running it for a while. It will repeat itself, so you may want to keep an eye on the various stages it goes through to know when it loops back to the beginning and starts over.

---

### Post by kainalu on 2009-01-17
this is running the live disk, i checked the memory yesterday for about 2hrs.


could this be the prob? free: 
Mem:        188664     186180       2484          0       2396      56904

---

### Post by caljohnsmith on 2009-01-17
> **kainalu said:**
> this is running the live disk, i checked the memory yesterday for about 2hrs.


could this be the prob? free: 
Mem:        188664     186180       2484          0       2396      56904
Yes, that definitely looks like the problem. If you only have 188 MB of memory, I don't think you can run Xubuntu. Better to stick with Puppy or another really lightweight distro.

---

### Post by kainalu on 2009-01-17
thanks for your help

--kainalu

---

