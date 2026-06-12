---
title: "Ubuntu, XP and Grub Problem"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by spynappels on 2009-01-14
Hi Guys,

I have a problem with an installation on my brother's Dell Inspiron 1525. I have installed Ubuntu 8.10 on it and then shrunk the partition and created another partition on which I have installed XP. Don't ask why I did it this way round.......

Anyway, I reinstalled grub after the XP install, but now Grub does not see the XP installation and does not give me the option of booting to it.

I have run the boot info script and the results are posted below.

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   217552229   108776083+  83  Linux
/dev/sda2   *   217552230   300495824    41471797+   7  HPFS/NTFS
/dev/sda3       300495825   312576704     6040440    5  Extended
/dev/sda5       300495888   312576704     6040408+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="629d4383-d151-4fa7-9a37-3a9d3bf631ec" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="CEC866E8C866CDF1" TYPE="ntfs" 
/dev/sda5: UUID="9d1904ce-c35e-411a-a05d-687fc27f7b77" TYPE="swap" 
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
# kopt=root=UUID=629d4383-d151-4fa7-9a37-3a9d3bf631ec ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=629d4383-d151-4fa7-9a37-3a9d3bf631ec

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
uuid		629d4383-d151-4fa7-9a37-3a9d3bf631ec
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=629d4383-d151-4fa7-9a37-3a9d3bf631ec ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		629d4383-d151-4fa7-9a37-3a9d3bf631ec
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=629d4383-d151-4fa7-9a37-3a9d3bf631ec ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		629d4383-d151-4fa7-9a37-3a9d3bf631ec
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=629d4383-d151-4fa7-9a37-3a9d3bf631ec ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		629d4383-d151-4fa7-9a37-3a9d3bf631ec
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=629d4383-d151-4fa7-9a37-3a9d3bf631ec ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		629d4383-d151-4fa7-9a37-3a9d3bf631ec
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=629d4383-d151-4fa7-9a37-3a9d3bf631ec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9d1904ce-c35e-411a-a05d-687fc27f7b77 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 23772
drwxr-xr-x  3 root root    4096 2009-01-14 15:40 .
drwxr-xr-x 20 root root    4096 2009-01-14 16:15 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-14 15:39 grub
-rw-r--r--  1 root root 8185238 2009-01-14 15:39 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8185337 2009-01-14 15:40 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-14 15:39 .
drwxr-xr-x 3 root root   4096 2009-01-14 15:40 ..
-rw-r--r-- 1 root root    197 2009-01-14 15:16 default
-rw-r--r-- 1 root root     15 2009-01-14 15:16 device.map
-rw-r--r-- 1 root root   8108 2009-01-14 15:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-14 15:16 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-14 15:16 installed-version
-rw-r--r-- 1 root root   8712 2009-01-14 15:16 jfs_stage1_5
-rw-r--r-- 1 root root   4792 2009-01-14 15:39 menu.lst
-rw-r--r-- 1 root root   4708 2009-01-14 15:39 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-14 15:16 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-14 15:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-14 15:16 stage1
-rw-r--r-- 1 root root 121460 2009-01-14 15:16 stage2
-rw-r--r-- 1 root root   9556 2009-01-14 15:16 xfs_stage1_5

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=============================== StdErr Messages: ===============================

No errors were reported.
```

Can someone help me to edit the menu so both XP and Ubuntu show up in the boot menu?

Thanks.

---

### Post by kranny on 2009-01-14
Why dont you change the lines referring to Xp boot lines in your menu.lst

```
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by spynappels on 2009-01-14
Thanks for that Kranny, but it did not do what I was expecting it to. 

I placed your code where it would be the second item on the boot list and saved the file, but when the computer reboots, I don't even get the option of picking any boot options, no Linux Kernel Blah Blah, Linux Kernel Blah Blah (Recovery Mode), Windows XP.

The computer just says grub stage 1.5, stage 2 and then Booting from (hd0,0) ext3.

Thanks for helping though.

---

### Post by kranny on 2009-01-14
Could you post your menu.lst..I am unable to follow the bootinfo scripts...Let see we could do something from there

---

### Post by spynappels on 2009-01-14
Ok, but my brother has had to go home, so I'll not be able to get that until tomorrow. Thanks for your help so far though.

Stefan.

---

### Post by ajgreeny on 2009-01-14
I am surprised that kranny's suggestion did not work for you, even though personally I would have added the windows entry after the memtest, but that is just because that's the way I usually see it.

OK, I've just looked in more detail and can see that you have the hiddenmenu uncommented in the 5th paragraph of the menu.lst file, so next boot, after you see the words "starting grub" on screen, you need to hit Esc quickly, you only have 3 seconds instead of the default 10.  If you want to always see the grub menu, comment out the word "hiddenmenu" in the file with a # at the start of the line and you will see the menu every boot, as most people do if they dual boot.  I think then you should be able to get into windows without problem.

---

### Post by kranny on 2009-01-14
> **spynappels said:**
> Thanks for that Kranny, but it did not do what I was expecting it to. 

I placed your code where it would be the second item on the boot list and saved the file, but when the computer reboots, I don't even get the option of picking any boot options, no Linux Kernel Blah Blah, Linux Kernel Blah Blah (Recovery Mode), Windows XP.

The computer just says grub stage 1.5, stage 2 and then Booting from (hd0,0) ext3.

Thanks for helping though.

> **spynappels said:**
> Ok, but my brother has had to go home, so I'll not be able to get that until tomorrow. Thanks for your help so far though.

Stefan.

Yeah try posting it after you get your laptop

---

