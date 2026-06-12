---
title: "Grub error 21"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by rugbylg6 on 2009-01-19
I have a home built desktop with a winxp and kubuntu hardy dual boot on one hard drive. I came into a 250 gb usb hard drive for cheap and descided to put xubuntu on it. I found instructions for installing it using the live cd. I booted the cd and installed it onto the hard drive, sdb, I then restared the computer per it's request. Everything seemed to go alright, I restarted again, unpluged the usb and attempted to boot kubuntu from my internal hard drive, sda, I recieved grub error 21 and now I cannot use winxp or kubuntu on my internal hard drive. The kubuntu live cd and the usb drive work perfectly. I'm sure I did something stupid so any help would be greatly appreciated. Thanks a ton.

---

### Post by meindian523 on 2009-01-19
You probably installed the Xubuntu Grub onto your USB HDD.What you need to do is plugin your USB HDD,and copy over the appropriate entries for Xubuntu onto the Grub installed onto your internal HDD.If Grub doesn't exist on the internal HDD,you would need to install it,with ```
setup (hd0)
``` at the Grub prompt which is obtained by ```
grub
``` at the terminal prompt,and then copy the entries for Xubuntu into the internal HDD menu.lst.

---

### Post by rugbylg6 on 2009-01-19
Entered command line in GRUB, I entered ```
setup (hd0)
``` and recieved ```
Checking if "/boot/grub/stage1" exists... yes
checking if "/boot/grub/stage2" exists... yes
checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/stage1 (hd0)" ... 16 sectors are embeded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage
 /boot/grub/menu.1st"... failed
Error 29 disk write error
```

---

### Post by caljohnsmith on 2009-01-19
Rugbylg6, in order to get a clearer picture of your setup, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the desktop, open a terminal/konsole and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by rugbylg6 on 2009-01-19
Alright, here it is. Sda is my internal, sdb is my external usb 
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for 
    /boot/grub/stage2nulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnuln
    ulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnuln
    ulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnul 
    and 0.97.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #256 for 
    /boot/grub/stage2nulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnuln
    ulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnuln
    ulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnulnul 
    and 0.97.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6cc46cc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   241890704   120945321    7  HPFS/NTFS
/dev/sda2       241890705   478287179   118198237+  83  Linux
/dev/sda3       478287180   488392064     5052442+   5  Extended
/dev/sda5       478287243   488392064     5052411   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   476648549   238324243+  83  Linux
/dev/sdb2       476648550   488392064     5871757+   5  Extended
/dev/sdb5       476648613   488392064     5871726   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4A44385744384849" TYPE="ntfs" 
/dev/sda2: UUID="4a2718ca-291a-4f22-a34c-e18182c3d160" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4d4b029f-ea84-47cf-b016-8dfc34f244ca" 
/dev/sdb1: UUID="b857d774-f4d7-45ed-9066-ebbc5da0fbfc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="c03a81ee-7852-4124-b2e6-2e79326c7d34" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

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
# kopt=root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro

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
# defoptions=quiet splash vga=791

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=4d4b029f-ea84-47cf-b016-8dfc34f244ca none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
<device> <mount\040point> auto users,noauto,atime,auto,rw,dev,exec,suid 0 0

================================== sda2/boot: ==================================

total 109312
drwxr-xr-x  3 root root    4096 2009-01-18 20:53 .
drwxr-xr-x 21 root root    4096 2009-01-18 20:52 ..
-rw-r--r--  1 root root  414274 2008-02-12 06:19 abi-2.6.20-16-generic
-rw-r--r--  1 root root  424317 2008-06-10 11:55 abi-2.6.22-15-generic
-rw-r--r--  1 root root  422667 2008-08-21 04:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 03:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 22:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   83217 2008-02-12 02:45 config-2.6.20-16-generic
-rw-r--r--  1 root root   75311 2008-06-10 11:55 config-2.6.22-15-generic
-rw-r--r--  1 root root   80049 2008-08-21 04:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 03:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 22:13 config-2.6.24-23-generic
drwxr-xr-x  3 root root    4096 2009-01-18 20:52 grub
-rw-r--r--  1 root root 7273712 2008-06-13 03:49 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 6928362 2008-03-01 12:32 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root 7281978 2008-06-20 18:10 initrd.img-2.6.22-15-generic
-rw-r--r--  1 root root 7282096 2008-06-20 18:09 initrd.img-2.6.22-15-generic.bak
-rw-r--r--  1 root root 7906624 2008-08-25 21:40 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7906830 2008-08-22 14:08 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7905816 2008-11-21 22:32 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7906015 2008-11-21 20:41 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7906261 2008-11-28 19:52 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7905856 2008-11-28 19:52 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7906293 2009-01-18 20:53 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7906158 2009-01-18 20:52 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  807071 2008-02-12 06:20 System.map-2.6.20-16-generic
-rw-r--r--  1 root root  823562 2008-06-10 11:55 System.map-2.6.22-15-generic
-rw-r--r--  1 root root  905170 2008-08-21 04:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 03:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 22:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1747532 2008-02-12 06:19 vmlinuz-2.6.20-16-generic
-rw-r--r--  1 root root 1764760 2008-06-10 11:55 vmlinuz-2.6.22-15-generic
-rw-r--r--  1 root root 1921464 2008-08-21 04:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 03:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 22:13 vmlinuz-2.6.24-23-generic

=============================== sda2/boot/grub: ===============================

total 232
drwxr-xr-x 3 root root   4096 2009-01-18 20:52 .
drwxr-xr-x 3 root root   4096 2009-01-18 20:53 ..
-rw-r--r-- 1 root root    197 2007-09-08 20:33 default
-rw-r--r-- 1 root root     15 2007-09-08 20:33 device.map
-rw-r--r-- 1 root root   8660 2007-09-08 20:33 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-09-08 20:33 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-09-08 20:33 installed-version
-rw-r--r-- 1 root root   9152 2007-09-08 20:33 jfs_stage1_5
-rw-r--r-- 1 root root   6805 2009-01-18 20:52 menu.lst
-rw-r--r-- 1 root root   6365 2009-01-18 20:52 menu.lst~
-rw-r--r-- 1 root root   5015 2008-05-11 15:32 menu.lst.backup
-rw-r--r-- 1 root root   7860 2007-09-08 20:33 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-09-08 20:33 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-05-11 15:32 splashimages
-rw-r--r-- 1 root root    512 2007-09-08 20:33 stage1
-rw-r--r-- 1 root root 110132 2007-09-08 20:33 stage2
-rw-r--r-- 1 root root   9980 2007-09-08 20:33 xfs_stage1_5

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
# kopt=root=UUID=b857d774-f4d7-45ed-9066-ebbc5da0fbfc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b857d774-f4d7-45ed-9066-ebbc5da0fbfc

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
uuid		b857d774-f4d7-45ed-9066-ebbc5da0fbfc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b857d774-f4d7-45ed-9066-ebbc5da0fbfc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b857d774-f4d7-45ed-9066-ebbc5da0fbfc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b857d774-f4d7-45ed-9066-ebbc5da0fbfc ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b857d774-f4d7-45ed-9066-ebbc5da0fbfc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b857d774-f4d7-45ed-9066-ebbc5da0fbfc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b857d774-f4d7-45ed-9066-ebbc5da0fbfc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b857d774-f4d7-45ed-9066-ebbc5da0fbfc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b857d774-f4d7-45ed-9066-ebbc5da0fbfc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.22-15-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.22-15-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.20-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4a2718ca-291a-4f22-a34c-e18182c3d160 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=b857d774-f4d7-45ed-9066-ebbc5da0fbfc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=c03a81ee-7852-4124-b2e6-2e79326c7d34 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 23812
drwxr-xr-x  3 root root    4096 2009-01-19 15:30 .
drwxr-xr-x 20 root root    4096 2009-01-19 15:29 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-19 15:29 grub
-rw-r--r--  1 root root 8206129 2009-01-19 15:29 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8205827 2009-01-19 15:30 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-19 15:29 .
drwxr-xr-x 3 root root   4096 2009-01-19 15:30 ..
-rw-r--r-- 1 root root    197 2009-01-19 15:01 default
-rw-r--r-- 1 root root     30 2009-01-19 15:01 device.map
-rw-r--r-- 1 root root   8108 2009-01-19 15:01 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-19 15:01 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-19 15:01 installed-version
-rw-r--r-- 1 root root   8712 2009-01-19 15:01 jfs_stage1_5
-rw-r--r-- 1 root root   9620 2009-01-19 15:29 menu.lst
-rw-r--r-- 1 root root   9536 2009-01-19 15:29 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-19 15:01 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-19 15:01 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-19 15:01 stage1
-rw-r--r-- 1 root root 121460 2009-01-19 15:01 stage2
-rw-r--r-- 1 root root   9556 2009-01-19 15:01 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-19
How about trying:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
And please post the output of the commands before doing "quit."

---

### Post by rugbylg6 on 2009-01-19
```
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by caljohnsmith on 2009-01-19
That looks great, so if you set your BIOS to boot the sda drive, you should be able to boot into Windows or Kubuntu. If you set your BIOS to boot the sdb drive, you should be able to boot into your new Xubuntu install. Let me know if that works. Also, do you want to boot your Xubuntu drive from your Windows/Kubuntu drive, or vice-versa?

---

### Post by rugbylg6 on 2009-01-19
everything works great now, thanks for all your help. The only other thing I hoped to do was set aside a small section of the drive for use as a storage device by windows, would it be as easy as resizing the main xubuntu partition with gparted and setting up a fat32 in the open space?

---

### Post by caljohnsmith on 2009-01-19
> **rugbylg6 said:**
> everything works great now, thanks for all your help. The only other thing I hoped to do was set aside a small section of the drive for use as a storage device by windows, would it be as easy as resizing the main xubuntu partition with gparted and setting up a fat32 in the open space?
Sure, you gparted should work fine to shrink your Xubuntu install, and then you can make a data partition with that space. I would suggest using NTFS instead of FAT32, because linux has really good NTFS read/write support now; then you won't be limited to the max 4 GB file size limitation of a FAT32 file system. But if you don't plan on having any files bigger than 4 GB (like DVD ISOs), then FAT32 should be fine. Good luck and enjoy your new Xubuntu install. :)

---

