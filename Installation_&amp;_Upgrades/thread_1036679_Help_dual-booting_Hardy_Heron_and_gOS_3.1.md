---
title: "Help dual-booting Hardy Heron and gOS 3.1"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by areo on 2009-01-11
I installed gOS 3.1 on an external USB drive and would like to dual boot Ubuntu and gOS. I have an old PC and the BIOS does not support booting from USB. Although the gOS installation was successful, I am unable to see it as an option during boot. 

 The configuration is
/dev/sda1 (windows partition on internal HD)
/dev/sda2 (ext3 partition on internal HD that has Ubuntu Hardy Heron)
/dev/sdb1 (ext3 partition on external USB drive that has gOS)

 I tried to use super grub but could not find a way to boot from the USB drive. I would appreciate any help.

---

### Post by mikewhatever on 2009-01-11
Since the BIOS does not support booting from USB, you can't boot from the external HDD, nor do you need to. Just add the info about gOS by editing the menu.lst.

---

### Post by caljohnsmith on 2009-01-11
How about on start up when you get the Grub menu, press "c" to get the command line, and do:
```
grub> geometry (hd1)
```
And does that show your USB drive? It should list the drive size and the partitions on that drive. If the command does show your USB drive, you can probably boot it with Grub. If the command returns an error though, you might be able to use Grub to boot a boot manager like "PLoP" that should allow you to then boot the USB drive. But let me know first what you get from the above command.

Also, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by yue232qi121 on 2009-01-11
is [runescape power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) safe??every one know.

---

### Post by areo on 2009-01-12
The output of the "geometry" command for hd1 is:

Error 21: Selected disk does not exist

I have attached below the output of the bootinfoscript. Note that I manually added the 3 selections for gOS to the top of menu.lst. I also copied the initrd.img, vmlinuz and System.map files from gOS and placed them in the /boot directory of hd0.

```

 ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. No 
                       errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d1adc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29061584    14530761    c  W95 FAT32 (LBA)
/dev/sda2        29061585    38973689     4956052+  83  Linux
/dev/sda3        38973690    40017914      522112+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d3e75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   156296384    78148161   83  Linux

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL=");^M^J  }^M^J}^M" UUID="2563-14EE" TYPE="vfat" 
/dev/sda2: UUID="36eb462d-e6a3-463d-8d72-913d726f619d" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="a718495b-59c9-45a2-8315-b27f27d22fc7" 
/dev/sdb1: UUID="b0ad648d-239e-4393-94bf-ff861a8e3cec" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

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
# kopt=root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		gOS, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0ad648d-239e-4393-94b
f-ff861a8e3cec ro quiet splash loglevel=0
initrd		/boot/initrd.img
quiet

title		gOS, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0ad648d-239e-4393-94b
f-ff861a8e3cec ro single
initrd		/boot/initrd.img

title		gOS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 8.04, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows 95/98/Me
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
UUID=36eb462d-e6a3-463d-8d72-913d726f619d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=2563-14EE  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=a718495b-59c9-45a2-8315-b27f27d22fc7 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
================================== sda2/boot: ==================================

total 103108
drwxr-xr-x  3 root root    4096 2009-01-11 06:08 .
drwxr-xr-x 21 root root    4096 2008-07-02 00:31 ..
-rw-r--r--  1 root root  285604 2006-10-13 12:09 abi-2.6.17-10-generic
-rw-r--r--  1 root root  414274 2007-09-23 13:28 abi-2.6.20-16-generic
-rw-r--r--  1 root root  424317 2008-02-12 02:39 abi-2.6.22-14-generic
-rw-r--r--  1 root root  422387 2008-03-12 18:43 abi-2.6.24-12-generic
-rw-r--r--  1 root root  422607 2008-04-10 09:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2009-01-11 06:07 abi-2.6.24-19-generic
-rw-r--r--  1 root root   74645 2006-10-13 09:13 config-2.6.17-10-generic
-rw-r--r--  1 root root   83217 2007-09-23 10:47 config-2.6.20-16-generic
-rw-r--r--  1 root root   75311 2008-02-12 02:39 config-2.6.22-14-generic
-rw-r--r--  1 root root   79746 2008-03-12 18:43 config-2.6.24-12-generic
-rw-r--r--  1 root root   79964 2008-04-10 09:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80049 2009-01-11 06:07 config-2.6.24-19-generic
drwxr-xr-x  2 root root    4096 2008-05-01 08:15 grub
-rw-r--r--  1 root root 7568626 2009-01-10 11:22 initrd.img
-rw-r--r--  1 root root 6442548 2007-10-21 08:59 initrd.img-2.6.17-10-generic
-rw-r--r--  1 root root 5443198 2007-10-21 07:13 initrd.img-2.6.17-10-generic.bak
-rw-r--r--  1 root root 6913491 2007-10-21 09:42 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 6841992 2007-10-21 09:24 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root 7252277 2008-03-22 11:11 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 7252624 2008-03-22 10:52 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root 7841218 2008-03-22 20:55 initrd.img-2.6.24-12-generic
-rw-r--r--  1 root root 7771681 2008-03-22 20:25 initrd.img-2.6.24-12-generic.bak
-rw-r--r--  1 root root 7568371 2008-05-01 08:50 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7568494 2008-05-01 08:15 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7866052 2009-01-11 06:08 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r--  1 root root  728690 2006-10-13 12:09 System.map-2.6.17-10-generic
-rw-r--r--  1 root root  807071 2007-09-23 13:30 System.map-2.6.20-16-generic
-rw-r--r--  1 root root  823535 2008-02-12 02:39 System.map-2.6.22-14-generic
-rw-r--r--  1 root root  903816 2008-03-12 18:43 System.map-2.6.24-12-generic
-rw-r--r--  1 root root  899892 2008-04-10 09:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905146 2009-01-11 06:08 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1636681 2006-10-13 12:09 vmlinuz-2.6.17-10-generic
-rw-r--r--  1 root root 1747372 2007-09-23 13:28 vmlinuz-2.6.20-16-generic
-rw-r--r--  1 root root 1764536 2008-02-12 02:39 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1909528 2008-03-12 18:43 vmlinuz-2.6.24-12-generic
-rw-r--r--  1 root root 1904248 2008-04-10 09:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1920472 2009-01-11 06:08 vmlinuz-2.6.24-19-generic

=============================== sda2/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2008-05-01 08:15 .
drwxr-xr-x 3 root root   4096 2009-01-11 06:08 ..
-rw-r--r-- 1 root root    197 2007-01-05 19:37 default
-rw-r--r-- 1 root root     15 2007-01-05 19:37 device.map
-rw-r--r-- 1 root root   7508 2007-01-05 19:37 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2007-01-05 19:37 fat_stage1_5
-rw-r--r-- 1 root root     16 2007-01-05 19:37 installed-version
-rw-r--r-- 1 root root   8128 2007-01-05 19:37 jfs_stage1_5
-rw-r--r-- 1 root root   6744 2009-01-11 00:21 menu.lst
-rw-r--r-- 1 root root   6052 2008-05-01 08:15 menu.lst~
-rw-r--r-- 1 root root   6804 2007-01-05 19:37 minix_stage1_5
-rw-r--r-- 1 root root   9076 2007-01-05 19:37 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-01-05 19:37 stage1
-rw-r--r-- 1 root root 105652 2007-01-05 19:37 stage2
-rw-r--r-- 1 root root   8764 2007-01-05 19:37 xfs_stage1_5

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
# kopt=root=UUID=b0ad648d-239e-4393-94bf-ff861a8e3cec ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash loglevel=0

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

title		gOS, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0ad648d-239e-4393-94bf-ff861a8e3cec ro quiet splash loglevel=0
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		gOS, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0ad648d-239e-4393-94bf-ff861a8e3cec ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		gOS, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-12-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single 
initrd		/boot/initrd.img-2.6.24-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.22-14-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.20-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.17-10-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=36eb462d-e6a3-463d-8d72-913d726f619d ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, memtest86+ (on /dev/sda2)
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
UUID=b0ad648d-239e-4393-94bf-ff861a8e3cec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=36eb462d-e6a3-463d-8d72-913d726f619d /oldlinux       ext3    relatime        0       2
# /dev/sda1
UUID=2563-14EE  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=a718495b-59c9-45a2-8315-b27f27d22fc7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 11088
drwxr-xr-x  3 root root    4096 2009-01-09 16:10 .
drwxr-xr-x 23 root root    4096 2009-01-09 16:09 ..
-rw-r--r--  1 root root  422667 2008-06-18 11:11 abi-2.6.24-19-generic
-rw-r--r--  1 root root   80049 2008-06-18 11:11 config-2.6.24-19-generic
drwxr-xr-x  2 root  999    4096 2009-01-09 16:10 grub
-rw-r--r--  1 root  999 7866052 2009-01-09 16:09 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r--  1 root root  905146 2008-06-18 11:11 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1920472 2008-06-18 11:11 vmlinuz-2.6.24-19-generic

=============================== sdb1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root  999   4096 2009-01-09 16:10 .
drwxr-xr-x 3 root root   4096 2009-01-09 16:10 ..
-rw-r--r-- 1 root  999    197 2009-01-09 16:10 default
-rw-r--r-- 1 root  999     30 2009-01-09 16:10 device.map
-rw-r--r-- 1 root  999   8056 2009-01-09 16:10 e2fs_stage1_5
-rw-r--r-- 1 root  999   7904 2009-01-09 16:10 fat_stage1_5
-rw-r--r-- 1 root  999     16 2009-01-09 16:10 installed-version
-rw-r--r-- 1 root  999   8608 2009-01-09 16:10 jfs_stage1_5
-rw-r--r-- 1 root root   8305 2009-01-09 16:11 menu.lst
-rw-r--r-- 1 root root   4252 2009-01-09 16:10 menu.lst~
-rw-r--r-- 1 root  999   7324 2009-01-09 16:10 minix_stage1_5
-rw-r--r-- 1 root  999   9632 2009-01-09 16:10 reiserfs_stage1_5
-rw-r--r-- 1 root  999    512 2009-01-09 16:10 stage1
-rw-r--r-- 1 root  999 108356 2009-01-09 16:10 stage2
-rw-r--r-- 1 root  999   9276 2009-01-09 16:10 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-12
OK, since the Grub geometry command on start up didn't even see your USB drive, I don't think there is much hope of booting it directly with Grub. But what might work is if you boot the PLoP boot manager with Grub, and then use PLoP to boot your USB drive. So to try that, how about booting into your Hardy Ubuntu install on sda2, and do the following:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
And please post the output of the above commands prior to doing "quit". Next download the [PLoP boot manager]("http://download.plop.at/files/bootmngr/plpbt-5.0rc18.zip") to your Ubuntu desktop and do:
```
cd ~/Desktop
unzip plp*.zip
sudo cp plp*/plpbt.bin /boot
gksudo gedit /boot/grub/menu.lst
```
And at the end of your menu.lst, after your Windows entry, add the following:
```
title PLoP Boot Manager
root (hd0,1)
kernel /boot/plpbt.bin
```
Then reboot, select "PLoP Boot Manager" from your Ubuntu Grub menu, and hopefully you will get the PLoP boot menu; choose the option to boot USB drive, and let me know exactly what happens. We can work from there.

---

### Post by areo on 2009-01-14
Hi CalJohnSmith,

 Thanks for the clear instructions. I was able to use PLoP to boot gOS. I appreciate all the help. Thanks!

 Areo

---

### Post by caljohnsmith on 2009-01-14
Glad to hear that worked OK; cheers and have fun with gOS 3.1. :)

---

