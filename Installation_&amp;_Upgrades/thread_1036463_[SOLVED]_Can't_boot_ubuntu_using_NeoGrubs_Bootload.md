---
title: "[SOLVED] Can't boot ubuntu using NeoGrubs Bootloader"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by ~farah_r~ on 2009-01-10
I seem to be running into problems one after the other in my ubuntu trial!!!

I am dual booting vista and ubuntu and both worked fine. But, I wanted to use Vista bootloader instead of GRUB, so I followed the steps in the following guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

Now, when I select NeoGrubs Bootloader, I get the error message:

Try (hd0,0): EXT2:

What did I do wrong, and more important, how do I fix it so I can get ubuntu back??

Thanks.

---

### Post by chex_m8 on 2009-01-10
Ok follow the directions in this link, you will need a flash drive for the procedure.
[LINK]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")
Also you need to reinstall the Vista boot loader to the MBR, you can use the EasyBCD program in vista to do so.

---

### Post by ~farah_r~ on 2009-01-10
> **chex_m8 said:**
> Ok follow the directions in this link, you will need a flash drive for the procedure.
[LINK]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")
Also you need to reinstall the Vista boot loader to the MBR, you can use the EasyBCD program in vista to do so.

I cant boot into Linux right now. So, can I go into Linux using the Ubuntu LiveCD with the try ubuntu without changing the computer option to do all the above guide says?

---

### Post by caljohnsmith on 2009-01-10
Instead of using NeoGrub, how about instead using EasyBCD to add the Ubuntu boot sector to the Vista boot menu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If that doesn't work either, it would help to get more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by chex_m8 on 2009-01-10
Sorry I should have mentioned that, yes you will be using the live CD.

---

### Post by ~farah_r~ on 2009-01-11
> **caljohnsmith said:**
> Instead of using NeoGrub, how about instead using EasyBCD to add the Ubuntu boot sector to the Vista boot menu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If that doesn't work either, it would help to get more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

I tried the EasyBCD. I do see the Linux option when the computer boots up but get errors when I click on Linux. Errors:

Loading New partition
Bootsector from C.H. Hochstatter
Cannot load from hard disk
Insert Systemdisk and press any key

This is what I get from the Boot Info Script:


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block. BootPart 
                       in the file /NST/nst_grub.mbr is trying to chain load 
                       sector #374796513 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot /NST

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda4: _________________________________________________________________________

    File system:       swap

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   156665879    78332908+  83  Linux
/dev/sda2   *   163413180   374795776   105691298+   7  HPFS/NTFS
/dev/sda3       374796450   390716864     7960207+   5  Extended
/dev/sda4       156665880   163413179     3373650   82  Linux swap / Solaris
/dev/sda5       374796513   390716864     7960176   82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 2 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 125 MB, 125829120 bytes
16 heads, 32 sectors/track, 480 cylinders, total 245760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf2a328f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32      245759      122864    e  W95 FAT16 (LBA)

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="62d7873b-345e-4b93-88fb-d8549099d549" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="E8CCC65ACCC62324" TYPE="ntfs" 
/dev/sda4: UUID="a406a425-36cb-416e-b74e-cb85326e14f6" TYPE="swap" 
/dev/sda5: UUID="423530eb-02b8-4fbf-970d-fc66170b2d20" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="FARAH" UUID="73C9-CBB5" TYPE="vfat" 

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
/dev/sdb1 on /media/FARAH type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

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
# kopt=root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=62d7873b-345e-4b93-88fb-d8549099d549

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
uuid		62d7873b-345e-4b93-88fb-d8549099d549
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		62d7873b-345e-4b93-88fb-d8549099d549
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		62d7873b-345e-4b93-88fb-d8549099d549
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62d7873b-345e-4b93-88fb-d8549099d549 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=a406a425-36cb-416e-b74e-cb85326e14f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11952
drwxr-xr-x  3 root root    4096 2009-01-10 20:21 .
drwxr-xr-x 20 root root    4096 2009-01-10 20:20 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-10 20:21 grub
-rw-r--r--  1 root root 8180631 2009-01-10 20:20 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-10 20:21 .
drwxr-xr-x 3 root root   4096 2009-01-10 20:21 ..
-rw-r--r-- 1 root root    197 2009-01-10 20:21 default
-rw-r--r-- 1 root root     30 2009-01-10 20:21 device.map
-rw-r--r-- 1 root root   8108 2009-01-10 20:21 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-10 20:21 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-10 20:21 installed-version
-rw-r--r-- 1 root root   8712 2009-01-10 20:21 jfs_stage1_5
-rw-r--r-- 1 root root   4619 2009-01-10 20:21 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-10 20:21 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-10 20:21 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-10 20:21 stage1
-rw-r--r-- 1 root root 121460 2009-01-10 20:21 stage2
-rw-r--r-- 1 root root   9556 2009-01-10 20:21 xfs_stage1_5

============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



## ## End Default Options ##



title		Ubuntu 8.10, kernel 2.6.27-7-generic

uuid		62d7873b-345e-4b93-88fb-d8549099d549

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro quiet splash 

initrd		/boot/initrd.img-2.6.27-7-generic

quiet



title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)

uuid		62d7873b-345e-4b93-88fb-d8549099d549

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro  single

initrd		/boot/initrd.img-2.6.27-7-generic



title		Ubuntu 8.10, memtest86+

uuid		62d7873b-345e-4b93-88fb-d8549099d549

kernel		/boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST
================================== sda2/Boot: ==================================

total 512
drwxrwxrwx 1 root root   4096 2009-01-11 06:51 .
drwxrwxrwx 1 root root   8192 2009-01-11 06:09 ..
-rwxrwxrwx 1 root root  28672 2009-01-11 06:09 BCD
-rwxrwxrwx 1 root root  25600 2009-01-11 06:09 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-11 06:51 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-11 06:51 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-11 06:51 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-11 06:51 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-11 06:51 da-DK
drwxrwxrwx 1 root root      0 2009-01-11 06:51 de-DE
drwxrwxrwx 1 root root      0 2009-01-11 06:51 el-GR
drwxrwxrwx 1 root root      0 2009-01-11 06:51 en-US
drwxrwxrwx 1 root root      0 2009-01-11 06:51 es-ES
drwxrwxrwx 1 root root      0 2009-01-11 06:51 fi-FI
drwxrwxrwx 1 root root      0 2009-01-11 06:51 Fonts
drwxrwxrwx 1 root root      0 2009-01-11 06:51 fr-FR
drwxrwxrwx 1 root root      0 2009-01-11 06:51 hu-HU
drwxrwxrwx 1 root root      0 2009-01-11 06:51 it-IT
drwxrwxrwx 1 root root      0 2009-01-11 06:51 ja-JP
drwxrwxrwx 1 root root      0 2009-01-11 06:51 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 09:51 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-11 06:51 nb-NO
drwxrwxrwx 1 root root      0 2009-01-11 06:51 nl-NL
drwxrwxrwx 1 root root      0 2009-01-11 06:51 pl-PL
drwxrwxrwx 1 root root      0 2009-01-11 06:51 pt-BR
drwxrwxrwx 1 root root      0 2009-01-11 06:51 pt-PT
drwxrwxrwx 1 root root      0 2009-01-11 06:51 ru-RU
drwxrwxrwx 1 root root      0 2009-01-11 06:51 sv-SE
drwxrwxrwx 1 root root      0 2009-01-11 06:51 tr-TR
drwxrwxrwx 1 root root      0 2009-01-11 06:51 zh-CN
drwxrwxrwx 1 root root      0 2009-01-11 06:51 zh-HK
drwxrwxrwx 1 root root      0 2009-01-11 06:51 zh-TW

================================== sda2/NST: ==================================

total 21
drwxrwxrwx 1 root root    0 2009-01-11 05:39 .
drwxrwxrwx 1 root root 8192 2009-01-11 06:09 ..
-rwxrwxrwx 1 root root  946 2009-01-11 03:22 menu.lst
-rwxrwxrwx 1 root root 8192 2008-04-08 17:50 NeoGrub.mbr
-rwxrwxrwx 1 root root  512 2009-01-11 05:39 nst_grub.mbr

================================ sdb1/menu.lst: ================================

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
# kopt=root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=62d7873b-345e-4b93-88fb-d8549099d549

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
uuid		62d7873b-345e-4b93-88fb-d8549099d549
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		62d7873b-345e-4b93-88fb-d8549099d549
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62d7873b-345e-4b93-88fb-d8549099d549 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		62d7873b-345e-4b93-88fb-d8549099d549
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-11
It looks like there are a couple of issues preventing you from booting Ubuntu from Vista right now. First, you should install Grub to the boot sector of your Ubuntu partition by doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
```
And please post the output prior to doing "quit." The other issue is that it looks like you added the wrong boot sector to your Vista boot menu; instead of adding the sda1 Ubuntu partition boot sector, it appears you added the sda5 swap partition boot sector by accident. So after doing the above Grub commands, how about using EasyBCD again to try and add the sda1 partition boot sector to your Vista boot loader, and not sda5.

Also, I just wanted to mention that you only need to have one swap partition, and an 8 GB swap partition (sda5) is really more than you would ever need. I would suggest deleting the sda5 swap partition and sticking with your 4 GB sda4 swap partition instead. Once you get Ubuntu booting OK, we can check to make sure your Ubuntu is using sda4 and not sda5 as swap. Anyway, let me know how it goes.

---

### Post by ~farah_r~ on 2009-01-11
> **caljohnsmith said:**
> It looks like there are a couple of issues preventing you from booting Ubuntu from Vista right now. First, you should install Grub to the boot sector of your Ubuntu partition by doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
```
And please post the output prior to doing "quit." The other issue is that it looks like you added the wrong boot sector to your Vista boot menu; instead of adding the sda1 Ubuntu partition boot sector, it appears you added the sda5 swap partition boot sector by accident. So after doing the above Grub commands, how about using EasyBCD again to try and add the sda1 partition boot sector to your Vista boot loader, and not sda5.

Also, I just wanted to mention that you only need to have one swap partition, and an 8 GB swap partition (sda5) is really more than you would ever need. I would suggest deleting the sda5 swap partition and sticking with your 4 GB sda4 swap partition instead. Once you get Ubuntu booting OK, we can check to make sure your Ubuntu is using sda4 and not sda5 as swap. Anyway, let me know how it goes.

IT WORKS!!! Finally, thanks a lot :)

---

### Post by lukedupree on 2009-03-06
I have a similar issue with the exception that the Vista boot loader sees the NeoGrub loader and then only boots into Grub. I have grub up but don't know how to get it to go ahead and boot into Ubuntu 8.10. Odd thing is I have done this before and it worked fine. I am using EasyBCD and have configured it several different ways according to the instructions but still boots into Grub only. I installed grub on the same partition as Ubuntu not the MBR as I don't want it to wipe out the Vista boot loader. I am also booting XP and it boots fine through Easy BCD.

I can't post my boot file or info because I can't get into linux actually. I could boot live but not sure what to do if I did.

Last time I configured NeoGrub to read the menulist for Linux but no luck, error 17.

Any Help here?

---

