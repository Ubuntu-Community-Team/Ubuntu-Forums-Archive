---
title: "Can't run Grub without Live CD??"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by dan1972 on 2008-12-30
Newbie help please!

I've installed Ubuntu8.04 on one HDD and its great.  WinXP still exists on the other HDD.  Grub ran and loaded properly for a while, then would only boot from the Live CD.

So now, every time I re-boot, the Live CD has to be loaded, choose language (Eng), the boot from First Hard Drive, this loads Grub , then can choose Ubuntu or WinXP.

If I restart with no Live CD in the PC the restart/power-on only gets to "Boot from CD/DVD" and hangs and hangs for ever.

Can any one help???

Thanks.

---

### Post by caljohnsmith on 2008-12-30
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by dan1972 on 2009-01-01
Thanks for your help - 

This is the contents of the Results.txt, its very long sorry.  Does this clarify anything??

Cheers.


[COLOR="Blue"]
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for its boot files.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc942c942

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398310   312576704   105089197+   f  W95 Ext'd (LBA)
/dev/sda5       102398373   312576704   105089166    7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00035287

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   468519659   234259798+  83  Linux
/dev/sdb2       468519660   488392064     9936202+   5  Extended
/dev/sdb5       468519723   488392064     9936171   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="96002B72002B588F" LABEL="System" TYPE="ntfs" 
/dev/sda5: UUID="26D8FE7DD8FE4A97" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: UUID="c70f5c58-2ecd-4415-93d2-fb1a4055d612" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="de8cdeea-7482-44fa-8d03-8de1c26bc84a" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/daniel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daniel)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=daniel)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c70f5c58-2ecd-4415-93d2-fb1a4055d612 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=de8cdeea-7482-44fa-8d03-8de1c26bc84a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 74532
drwxr-xr-x  3 root root    4096 Dec  8 18:39 .
drwxr-xr-x 21 root root    4096 Nov 28 18:08 ..
-rw-r--r--  1 root root  899892 Apr 11  2008 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905170 Aug 21 14:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 Oct 22 14:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 Nov 25 09:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  422607 Apr 11  2008 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 Aug 21 14:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 Oct 22 14:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 Nov 25 09:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   79964 Apr 11  2008 config-2.6.24-16-generic
-rw-r--r--  1 root root   80049 Aug 21 14:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 Oct 22 14:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 Nov 25 09:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 Nov 28 18:08 grub
-rw-r--r--  1 root root 7883389 Jun 28  2008 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7349268 Apr 23  2008 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7907709 Aug 27 20:59 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7907492 Aug 12 20:51 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7911746 Nov  8 17:28 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7911620 Nov  2 19:16 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7907964 Dec  8 18:39 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7909003 Nov 28 18:08 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 Sep 28  2007 memtest86+.bin
-rw-r--r--  1 root root 1904248 Apr 11  2008 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921464 Aug 21 14:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 Oct 22 14:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 Nov 25 09:47 vmlinuz-2.6.24-22-generic

=============================== sdb1/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 Nov 28 18:08 .
drwxr-xr-x 3 root root   4096 Dec  8 18:39 ..
-rw-r--r-- 1 root root    197 Jun 28  2008 default
-rw-r--r-- 1 root root     30 Jun 28  2008 device.map
-rw-r--r-- 1 root root   8056 Jun 28  2008 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 Jun 28  2008 fat_stage1_5
-rw-r--r-- 1 root root     16 Jun 28  2008 installed-version
-rw-r--r-- 1 root root   8608 Jun 28  2008 jfs_stage1_5
-rw-r--r-- 1 root root   5878 Nov 28 18:08 menu.lst
-rw-r--r-- 1 root root   5446 Nov 28 18:08 menu.lst~
-rw-r--r-- 1 root root   7324 Jun 28  2008 minix_stage1_5
-rw-r--r-- 1 root root   9632 Jun 28  2008 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 Jun 28  2008 stage1
-rw-r--r-- 1 root root 108356 Jun 28  2008 stage2
-rw-r--r-- 1 root root   9276 Jun 28  2008 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sdb

00000000  fa b8 00 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |................|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  87 52 03 00 00 00 00 01  |.........R......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 ad 0a ed 1b 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff ec 0a  ed 1b 95 3a 2f 01 00 00  |...........:/...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.
```[/COLOR]

---

### Post by caljohnsmith on 2009-01-01
OK, according to the script output, you have Grub correctly installed to your Windows sda drive, so if you are having trouble booting it, it sounds like it might be a BIOS issue. Can you go into your BIOS and check the boot order of drives? Since your Linux sdb drive does not currently have a boot loader in its MBR (Master Boot Record), I suspect that maybe your problem is that you have your BIOS set to boot the Linux sdb drive before the Windows sda drive. I would temporarily change the boot order so that the Windows drive comes before even your CD/DVD drive, and see if you can get the Windows drive to boot that way. Or another option is to install Grub to your Linux sdb drive and just boot your sdb drive on start up; that is actually more ideal, because then your drives won't be dependent on each other for booting. If you want to try that, just do:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
That will install Grub to the MBR of your Linux sdb drive, and then you should be able to boot it. If you decide to boot the sdb drive, you will have to make a few slight modifications to your Grub's menu.lst to get it fully working, but you can at least test if booting the sdb drive works by seeing if you get the Grub menu on start up when booting the sdb drive. Let me know how it goes or if you run into problems, and we can work from there.

---

