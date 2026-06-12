---
title: "Hanging Install"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by kunks112 on 2009-01-20
I have installed Ubuntu 8.04 from a purchased cd to a fresh 500 GB SATA drive. On another 300 GB SATA drive I have Windows Vista and on another miscellaneous 100 GB IDE drive I have storage of data files.

My problem is that after the installation on Ubuntu, and setting my boot priority to SATA 3 (drive of Ubuntu), my screen displays the following

GRUB:_

I cannot type in anything, nor does any option appear after a 30 minute wait time.

Can I please get some assistance?

Thanks
Mike

---

### Post by caljohnsmith on 2009-01-20
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by kunks112 on 2009-01-20
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub is installed in the MBR of /dev/sdc and looks at sector 21591 on boot 
    drive #1 for the stage2 file, but no stage2 files can be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /ntldr /NTDETECT.COM /Boot

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       swap

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3eee3eed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195350399    97675168+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bf61bf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   586051199   293025568+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009aac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   955498004   477748971   83  Linux
/dev/sdc2       955498005   976768064    10635030    5  Extended
/dev/sdc5       955498068   976768064    10634998+  82  Linux swap / Solaris

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 4102 MB, 4102887936 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8013453 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009305c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          34     7984304     3992135+   b  W95 FAT32

sfdisk -V /dev/sdd:

/dev/sdd: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3A64AAB364AA7175" TYPE="ntfs" 
/dev/sdb1: UUID="40BC2AF2BC2AE1E0" TYPE="ntfs" 
/dev/sdc1: UUID="83f4c8c5-84d0-4741-a528-d10bf6a673dd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="62132145-d060-460c-afeb-3d7dd27bfadc" TYPE="swap" 
/dev/sdd1: UUID="200D-D515" TYPE="vfat" 
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
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================== sdb1/Boot: ==================================

total 784
drwxrwxrwx 1 root root   4096 2008-07-04 17:25 .
drwxrwxrwx 1 root root  28672 2009-01-20 07:09 ..
-rwxrwxrwx 1 root root  28672 2009-01-21 03:11 BCD
-rwxrwxrwx 1 root root 262144 2009-01-21 02:48 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-03-14 07:30 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-03-14 07:30 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-03-13 23:03 bootstat.dat
drwxrwxrwx 1 root root      0 2008-07-04 17:25 cs-CZ
drwxrwxrwx 1 root root      0 2008-07-04 17:25 da-DK
drwxrwxrwx 1 root root      0 2008-07-04 17:25 de-DE
drwxrwxrwx 1 root root      0 2008-07-04 17:25 el-GR
drwxrwxrwx 1 root root      0 2008-07-04 17:25 en-US
drwxrwxrwx 1 root root      0 2008-07-04 17:25 es-ES
drwxrwxrwx 1 root root      0 2008-07-04 17:25 fi-FI
drwxrwxrwx 1 root root   4096 2008-07-04 17:25 Fonts
drwxrwxrwx 1 root root      0 2008-07-04 17:25 fr-FR
drwxrwxrwx 1 root root      0 2008-07-04 17:25 hu-HU
drwxrwxrwx 1 root root      0 2008-07-04 17:25 it-IT
drwxrwxrwx 1 root root      0 2008-07-04 17:25 ja-JP
drwxrwxrwx 1 root root      0 2008-07-04 17:25 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-07-04 17:25 nb-NO
drwxrwxrwx 1 root root      0 2008-07-04 17:25 nl-NL
drwxrwxrwx 1 root root      0 2008-07-04 17:25 pl-PL
drwxrwxrwx 1 root root      0 2008-07-04 17:25 pt-BR
drwxrwxrwx 1 root root      0 2008-07-04 17:25 pt-PT
drwxrwxrwx 1 root root      0 2008-07-04 17:25 ru-RU
drwxrwxrwx 1 root root      0 2008-07-04 17:25 sv-SE
drwxrwxrwx 1 root root      0 2008-07-04 17:25 tr-TR
drwxrwxrwx 1 root root      0 2008-07-04 17:25 zh-CN
drwxrwxrwx 1 root root      0 2008-07-04 17:25 zh-HK
drwxrwxrwx 1 root root      0 2008-07-04 17:25 zh-TW

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=83f4c8c5-84d0-4741-a528-d10bf6a673dd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=83f4c8c5-84d0-4741-a528-d10bf6a673dd ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=83f4c8c5-84d0-4741-a528-d10bf6a673dd ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=83f4c8c5-84d0-4741-a528-d10bf6a673dd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=62132145-d060-460c-afeb-3d7dd27bfadc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 18280
drwxr-xr-x  3 root root      4096 2009-01-17 19:28 .
drwxr-xr-x 21 root root      4096 2009-01-17 19:28 ..
-rw-r--r--  1 root root    422607 2008-04-10 16:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root     79964 2008-04-10 16:51 config-2.6.24-16-generic
drwxr-xr-x  2 root ubuntu    4096 2009-01-17 19:28 grub
-rw-r--r--  1 root ubuntu 7886501 2009-01-17 19:28 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root   7349268 2008-04-22 18:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root    899892 2008-04-10 16:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root   1904248 2008-04-10 16:51 vmlinuz-2.6.24-16-generic

=============================== sdc1/boot/grub: ===============================

total 212
drwxr-xr-x 2 root ubuntu   4096 2009-01-17 19:28 .
drwxr-xr-x 3 root root     4096 2009-01-17 19:28 ..
-rw-r--r-- 1 root ubuntu    197 2009-01-17 19:28 default
-rw-r--r-- 1 root ubuntu     90 2009-01-17 19:28 device.map
-rw-r--r-- 1 root ubuntu   8056 2009-01-17 19:28 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2009-01-17 19:28 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2009-01-17 19:28 installed-version
-rw-r--r-- 1 root ubuntu   8608 2009-01-17 19:28 jfs_stage1_5
-rw-r--r-- 1 root root     4810 2009-01-17 19:28 menu.lst
-rw-r--r-- 1 root root     4276 2009-01-17 19:28 menu.lst~
-rw-r--r-- 1 root ubuntu   7324 2009-01-17 19:28 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2009-01-17 19:28 reiserfs_stage1_5
-rw-r--r-- 1 root ubuntu    512 2009-01-17 19:28 stage1
-rw-r--r-- 1 root ubuntu 108356 2009-01-17 19:28 stage2
-rw-r--r-- 1 root ubuntu   9276 2009-01-17 19:28 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-21
That's interesting, how did you install Grub to your Ubuntu sdc drive? It looks like Grub was installed to the MBR (Master Boot Record), but Grub was installed without its stage1.5 file that normally is embedded in the sectors right after the MBR; instead Grub points directly to the stage2 file. One way to do that is with a special install command in the Grub CLI, but I'm just wondering how you did it? How about trying this:
```
sudo grub
grub> root (hd2,0)
grub> makeactive
grub> setup (hd2)
grub> quit
```
Also do:
```
sudo mount /dev/sdc1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,0) instead of (hd2,0), similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=83f4c8c5-84d0-4741-a528-d10bf6a673dd ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```
And lastly change the "# groot" line to:
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
Save, reboot, make sure your BIOS is set to boot the Ubuntu drive, and let me know exactly what happens. We can work from there.

---

### Post by kunks112 on 2009-01-21
To answer you question while sounding like a total linux noob, I dont know how it was installed the way it was. I just inserted disk, booted in graphics safe mode, and installed from desktop whle running from cd. The only parameter I changed was where ubuntu was going to be installed.

Now to sound more like a linux noob, where exactly do i put those command line in? I insert live disk then.......

Thank you for the help so far.

---

### Post by caljohnsmith on 2009-01-21
> **kunks112 said:**
> To answer you question while sounding like a total linux noob, I dont know how it was installed the way it was. I just inserted disk, booted in graphics safe mode, and installed from desktop whle running from cd. The only parameter I changed was where ubuntu was going to be installed.

Now to sound more like a linux noob, where exactly do i put those command line in? I insert live disk then.......

Thank you for the help so far.
No problem, just boot the Live CD again, choose the "try Ubuntu without making changes" type option, and once you get to the desktop again, open a terminal (Applications > Accessories > Terminal). There you can enter all the commands. :)

---

### Post by kunks112 on 2009-01-21
In the terminal window, I type the following and get the following back


grub> root (hd2,0)
grub> makeactive
grub> setup (hd2)
  Checking if "/boot/grub/stage1" exists... no
  Checking if "/grub/stage1" exists... no

Error 15: File not found

---

### Post by caljohnsmith on 2009-01-21
It looks like the device names of your drives might be changing since those Grub commands didn't work. How about doing:
```
sudo fdisk -lu
```
Check which is the Ubuntu drive (it was sdc previously), and then do:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sdc[/COLOR]
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
```
Change sdc in the above commands if the Ubuntu drive is a different drive name, and please post the output of all the above commands.

---

### Post by kunks112 on 2009-01-21
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009aac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   955498004   477748971   83  Linux
/dev/sdb2       955498005   976768064    10635030    5  Extended
/dev/sdb5       955498068   976768064    10634998+  82  Linux swap / Solaris
```
 From this I used sdb, I'm not sure why it switched, maybe a problem to tackle another day.

As to the input output:
```
grub> device (hd0) /dev/sdb

grub> root (hd0,0)

grub> makeactive

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu
.lst"... succeeded
Done.

grub> quit
```

I would continue with the steps outlined above in your previous post, however I am unsure of why sdc1 was mounted. Now that I am in sdb, I don't want to go ahead.

---

### Post by caljohnsmith on 2009-01-21
Great, so proceed with the rest of the commands from post #4, but use "sdb1" instead of "sdc1" with the mount command. Let me know how that goes or if you run into problems.

---

### Post by kunks112 on 2009-01-21
I am currently writing this post from my new OS not loaded with the CD. Success!

Thank you for all the valuable assistance. If I would have known problems could be fixed this timely with an Linux OS, I would have quit Microsoft years ago.

Time for the updates, drivers, and all the rest of the great joys of configuration.

Once again
 Thanks

---

### Post by caljohnsmith on 2009-01-21
Glad to hear you booted into Ubuntu OK; good luck with all the configuring, cheers and have fun with Ubuntu. :)

---

### Post by kunks112 on 2009-01-21
Now the only issue I have is that when in the boot loader, the Vista/Longhorn (loader) loads XP, and the XP loader loads nothing but error 13.

---

### Post by caljohnsmith on 2009-01-22
So what do you mean exactly? When you boot the Vista entry in Grub, do you get the Vista boot menu where you can choose between Vista and XP? Or do get the error 13 before that? Also, is the error 13 a Grub error or a Windows error? I might guess it is a Grub error, but I don't know if Windows uses the same error code. Also, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the bottom the following entry:
```
title Windows (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, and let me know what happens when you choose the above entry from the Grub menu. We can work from there.

---

### Post by kunks112 on 2009-01-22
You are fantastic at helping. That one extra segment of code worked properly.

So under the same logic, can I remove the menu option of "Win XP" by deleting the entry and rename "vista longhorn" to "Xp"

---

### Post by caljohnsmith on 2009-01-23
> **kunks112 said:**
> You are fantastic at helping. That one extra segment of code worked properly.

So under the same logic, can I remove the menu option of "Win XP" by deleting the entry and rename "vista longhorn" to "Xp"
Sure, that sounds like a good plan. Cheers and enjoy all your OSes. :)

---

