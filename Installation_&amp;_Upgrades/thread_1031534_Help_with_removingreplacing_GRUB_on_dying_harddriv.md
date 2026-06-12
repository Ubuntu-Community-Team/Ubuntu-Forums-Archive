---
title: "Help with removing/replacing GRUB on dying harddrive"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by The Real Napsta on 2009-01-05
Here's my  situation:

I have an Ubuntu/Windows Xp dual boot. Each OS has it's own physical harddrive. Xp is on a 100gb HDD and ubuntu is my on 20gb.

The 20gb has the GRUB bootloader on it. The 20gb HD is also dying. (I can still get it to work after multiple tries as of now)

I need help getting Windows to boot on it's own without the GRUB and the 2nd (ubuntu harddrive). 

Keep in mind that the GRUB is on the lunux harddrive and not the XP drive. 

I can access the Xp drive from ubuntu but I don't think i can access the ubuntu drive from Xp.

Any help would be great, thanks for reading.

---

### Post by caljohnsmith on 2009-01-05
Have you tried changing your BIOS to boot the Windows drive? If so, what happens? Do you have a Ubuntu Live CD you can use for troubleshooting? If you do, how about booting that, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo xxd -l 2 -p /dev/sda
sudo xxd -l 2 -p /dev/sdb
```
That will help determine if Grub is maybe in the MBR (Master Boot Record) of your Windows drive. Please post the output and we can work from there if you want.

---

### Post by The Real Napsta on 2009-01-05
```
sudo xxd -l 2 -p /dev/sda
fa33
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdb
xxd: /dev/sdb: No such file or directory

```

That's the output I got. Thanks for the help so far.

---

### Post by caljohnsmith on 2009-01-05
OK, I see I'm going to need a bit more info about your setup since your sdb drive was not even found; how about running:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by donkyhotay on 2009-01-05
It's only showing one drive, lets see if we can find it. What are the results of 
```
ls -la | grep 'sd'
```
?

//edit: never mind, caljohnsmith's script should provide us with the information we need better then grepping your devices.

---

### Post by The Real Napsta on 2009-01-05
Sorry I took so long to respond.

Here's the results.txt: 

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/hda and looks on boot drive #2 in 
    partition #1 for its boot files.
 => Windows is installed in the MBR of /dev/hdb
 => No boot loader is installed in the MBR of /dev/hdc
 => No known boot loader is installed in the MBR of /dev/hdd
 => No boot loader is installed in the MBR of /dev/sda

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

hda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

hdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Win_98
    Boot sector info:  According to the info in the boot sector, hdb1 has 
                       39100257 sectors, but according to the info from 
                       fdisk, it has 37431386 sectors.
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

hdb2: _________________________________________________________________________

    File system:       Extended Partition

hdb5: _________________________________________________________________________

    File system:       swap

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSDOS5.0: Fat 16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive hda: _____________________________________________________________________

fdisk -lu /dev/hda:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *     9767520   195366464    92799472+   7  HPFS/NTFS
/dev/hda2              63     9767519     4883728+   b  W95 FAT32

Partition table entries are not in disk order

sfdisk -V /dev/hda:

/dev/hda: OK

Drive hdb: _____________________________________________________________________

fdisk -lu /dev/hdb:

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    37431449    18715693+  83  Linux
/dev/hdb2        37431450    39102209      835380    5  Extended
/dev/hdb5        37431513    39102209      835348+  82  Linux swap / Solaris

sfdisk -V /dev/hdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 1 does not end at a cylinder boundary

Drive hdc: _____________________________________________________________________

fdisk -lu /dev/hdc:
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 732 MB, 732293120 bytes
255 heads, 63 sectors/track, 22 cylinders, total 357565 sectors
Units = sectors of 1 * 2048 = 2048 bytes


sfdisk -V /dev/hdc:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/hdc: unrecognized partition table type

sfdisk: no partition table present.

Drive hdd: _____________________________________________________________________

fdisk -lu /dev/hdd:

sfdisk -V /dev/hdd:

read: Input/output error

sfdisk: read error on /dev/hdd - cannot read sector 0
 /dev/hdd: unrecognized partition table type

sfdisk: no partition table present.

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders, total 501759 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              99      501247      250574+   6  FAT16

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/hda1: TYPE="ntfs" 
/dev/hda2: LABEL="           FAT32   ‹ÐÁâ€æfÁèf;Føt*f‰FøfFôf¶^(€ãt:^ƒ" UUID="423B-2BDF" TYPE="vfat" 
/dev/hdb1: UUID="54afcc28-e1a5-4429-841b-b0ff036752c9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: TYPE="swap" UUID="a3483db5-f5af-4686-b546-f8429a2eea14" 
/dev/sda1: SEC_TYPE="msdos" UUID="3B69-1AFD" TYPE="vfat" 

=============================== "mount" output: ===============================

unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)

================================ hda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== hdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== hdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=54afcc28-e1a5-4429-841b-b0ff036752c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=a3483db5-f5af-4686-b546-f8429a2eea14 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
================================== hdb1/boot: ==================================

total 47484
drwxr-xr-x  3 root root    4096 2008-04-10 14:40 .
drwxr-xr-x 21 root root    4096 2007-07-26 17:36 ..
-rw-r--r--  1 root root  285721 2006-12-05 22:47 abi-2.6.17-10-generic
-rw-r--r--  1 root root  285721 2007-05-18 23:57 abi-2.6.17-11-generic
-rw-r--r--  1 root root  285721 2007-07-16 19:57 abi-2.6.17-12-generic
-rw-r--r--  1 root root  414274 2008-02-12 06:19 abi-2.6.20-16-generic
-rw-r--r--  1 root root   74707 2006-12-05 21:20 config-2.6.17-10-generic
-rw-r--r--  1 root root   74707 2007-05-18 22:31 config-2.6.17-11-generic
-rw-r--r--  1 root root   74707 2007-07-16 18:30 config-2.6.17-12-generic
-rw-r--r--  1 root root   83217 2008-02-12 02:45 config-2.6.20-16-generic
drwxr-xr-x  2 root root    4096 2008-04-10 14:40 grub
-rw-r--r--  1 root root 5455011 2007-04-06 19:53 initrd.img-2.6.17-10-generic
-rw-r--r--  1 root root 5454826 2007-05-28 14:55 initrd.img-2.6.17-11-generic
-rw-r--r--  1 root root 6836572 2007-07-26 17:33 initrd.img-2.6.17-12-generic
-rw-r--r--  1 root root 5514966 2007-07-26 16:41 initrd.img-2.6.17-12-generic.bak
-rw-r--r--  1 root root 6914322 2008-04-10 14:40 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 6913417 2008-01-12 18:37 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root   94600 2006-10-20 11:44 memtest86+.bin
-rw-r--r--  1 root root  728778 2006-12-05 22:47 System.map-2.6.17-10-generic
-rw-r--r--  1 root root  729932 2007-05-18 23:57 System.map-2.6.17-11-generic
-rw-r--r--  1 root root  729954 2007-07-16 19:57 System.map-2.6.17-12-generic
-rw-r--r--  1 root root  807071 2008-02-12 06:20 System.map-2.6.20-16-generic
-rw-r--r--  1 root root 1636700 2006-12-05 22:47 vmlinuz-2.6.17-10-generic
-rw-r--r--  1 root root 1636016 2007-05-18 23:57 vmlinuz-2.6.17-11-generic
-rw-r--r--  1 root root 1636514 2007-07-16 19:57 vmlinuz-2.6.17-12-generic
-rw-r--r--  1 root root 1747532 2008-02-12 06:19 vmlinuz-2.6.20-16-generic

=============================== hdb1/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2008-04-10 14:40 .
drwxr-xr-x 3 root root   4096 2008-04-10 14:40 ..
-rw-r--r-- 1 root root    197 2007-04-04 22:16 default
-rw-r--r-- 1 root root     30 2007-04-04 22:16 device.map
-rw-r--r-- 1 root root   7508 2007-04-04 22:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2007-04-04 22:16 fat_stage1_5
-rw-r--r-- 1 root root     16 2007-04-04 22:16 installed-version
-rw-r--r-- 1 root root   8128 2007-04-04 22:16 jfs_stage1_5
-rw-r--r-- 1 root root   5939 2008-04-10 14:40 menu.lst
-rw-r--r-- 1 root root   5939 2008-04-10 14:40 menu.lst~
-rw-r--r-- 1 root root   6804 2007-04-04 22:16 minix_stage1_5
-rw-r--r-- 1 root root   9076 2007-04-04 22:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-04-04 22:16 stage1
-rw-r--r-- 1 root root 105652 2007-04-04 22:16 stage2
-rw-r--r-- 1 root root   8764 2007-04-04 22:16 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/hdd


Unknown BootLoader  on /dev/hda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  20 0a 95 00 30 25 00 00  00 00 00 00 02 00 00 00  | ...0%..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 df 2b 3b 42 20  20 20 20 20 20 20 20 20  |..).+;B         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  cc 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 53 54 4c 44 52 20 20  |.f..f.F..STLDR  |
000001b0  20 20 20 20 0d 0a 49 6e  76 61 6c 69 64 20 53 79  |    ..Invalid Sy|
000001c0  73 74 65 6d 20 44 69 73  6b 20 6f 72 0d 0a 44 69  |stem Disk or..Di|
000001d0  73 6b 20 49 2f 4f 20 65  72 72 6f 72 0d 0a 50 72  |sk I/O error..Pr|
000001e0  65 73 73 20 61 20 6b 65  79 20 74 6f 20 72 65 73  |ess a key to res|
000001f0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 55 aa  |tart..........U.|
00000200


=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Disk /dev/hdc doesn't contain a valid partition table

```

---

### Post by caljohnsmith on 2009-01-06
OK, to restore a Windows MBR to your Windows hda drive, how about doing:
```
sudo apt-get install lilo
sudo lilo -M  /dev/hda mbr
```
Then reboot, try to boot the hda Windows drive, and you should be able to boot straight into Windows. Let me know how it goes or if you run into problems.

---

### Post by The Real Napsta on 2009-01-06
Do that using my live cd correct?

---

### Post by caljohnsmith on 2009-01-06
> **The Real Napsta said:**
> Do that using my live cd correct?
You could actually run those commands from your Ubuntu install, but considering that you said your 20 GB Ubuntu drive is dying, I would recommend using the Live CD instead. :)

---

### Post by The Real Napsta on 2009-01-06
Okay I'll try it and let you know what happens. Thanks again for all the help.

---

### Post by The Real Napsta on 2009-01-06
It didn't work, it failed to grab the files from the ubuntu site.

---

### Post by caljohnsmith on 2009-01-06
Did you try running the second lilo command anyway? The Intrepid CD comes with lilo, so you actually don't have to install it if you are using an Intrepid Live Cd; I'm not sure whether previous Ubuntu Live CDs come with lilo, so that's why I included the apt-get command in case the Live CD you were using didn't have it all ready. Also, you were able to download the script from the internet and run that OK from the Live CD, so I'm wondering why apt-get would fail.

If you have a Windows Install CD though, you could just use that, go to the "recovery console", and run:
```
fixmbr
```
And that should do the trick. Or another option is to download the [Super Grub Disk]("http://www.supergrubdisk.org") and use it to install a Windows MBR. Let me know how it goes or if you run into problems.

---

### Post by The Real Napsta on 2009-01-06
```
sudo apt-get install lilo
sudo lilo -M  /dev/hda mbr
```

Tried that code again with my LIVE CD today and it worked. Windows boots without the dead/dying harddrive. Thank you so much for all of your help and dealing with a newb like me lol.

Again, Thanks.

---

### Post by caljohnsmith on 2009-01-06
Glad to hear that worked OK and you can boot Windows now. Cheers and Happy New Year. :)

---

