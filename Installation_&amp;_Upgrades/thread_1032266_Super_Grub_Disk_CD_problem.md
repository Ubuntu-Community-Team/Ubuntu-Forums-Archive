---
title: "Super Grub Disk CD problem"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by pontuz2 on 2009-01-06
Hello again!
I've got some strange problems with GRUB etc...
so i will try SGD.

When i boot from the Super Grub Disk Cdrom everything is okay, but when i am in the GNU/Linux menu (Fix Boot of Gnu/Linux (GRUB), Boot Gnu/Linux, Boot Gnu/Linux Directly, Gnu/Linux (Advanced))
and select something it just flashes a blue menu and then it stands "selectfile XXX" where X is some path to some file.

I've also tried other verions of SGD with the same problem.

Thanks for help!

---

### Post by Pumalite on 2009-01-06
[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

---

### Post by pontuz2 on 2009-01-06
Yes, but when i click on "Fix Boot of Gnu/Linux (GRUB)" it just flashes a menu and then it disappear. I can't choose any partition to fix the GRUB.

I've also tried it via the command line.

---

### Post by Pumalite on 2009-01-06
Burn a new Super Grub CD after doing md5sum on the iso. Do not use CD-RW. Clean the lens in your burner.

---

### Post by pontuz2 on 2009-01-06
Ok, i am using a CD-RW so maby it's the problem.

How do i md5sum the iso?

---

### Post by Pumalite on 2009-01-06
[http://etree.org/md5com.html](http://etree.org/md5com.html)
Also check the link I gave you.

---

### Post by pontuz2 on 2009-01-06
Tried that but it doesn't work... Same problem.

---

### Post by Pumalite on 2009-01-06
Try the disk in a different computer.

---

### Post by pontuz2 on 2009-01-06
Oh no, it works perfectly on the other computer. It must be a problem on this computer. I don't understand, this computer is almost brand new. Do you think it's a problem on the computer?

---

### Post by Pumalite on 2009-01-06
Can you boot a Live CD? If yes; post:
sudo fdisk -lu
Post your specs.

---

### Post by pontuz2 on 2009-01-06
sudo fdisk -lu should be in here:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sdb1 and 
                       looks at sector 1425471 of the same hard drive for the 
                       stage2 file (a stage2 file is at this location on 
                       /dev/sdb) and on partition #1 for menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320,0 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar, totalt 625142448 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0xd0e69577

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1              63    22523129    11261533+  12  Compaq-diagnostik
/dev/sda2   *    22523904   324081663   150778880    7  HPFS/NTFS
/dev/sda3       324095310   618293654   147099172+   7  HPFS/NTFS
/dev/sda4       618299392   625139711     3420160   12  Compaq-diagnostik

sfdisk -V /dev/sda:

Varning: partition 4 fortsätter utanför hårddisken

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 1000,2 GB, 1000204886016 byte
255 huvuden, 63 sektorer/spår, 121601 cylindrar, totalt 1953525168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0x000d290e

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1   *          63     3903794     1951866   83  Linux
/dev/sdb2         3903795    50781464    23438835    5  Utökad
/dev/sdb5         3903858     7807589     1951866   82  Linux växling / Solaris
/dev/sdb6         7807653    27342629     9767488+  83  Linux
/dev/sdb7        27342693    50781464    11719386   83  Linux

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1C6ACCCBE49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="4EC8E1278406103C" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="1CD1630028EEDA4B" TYPE="ntfs" 
/dev/sda4: UUID="666C87906C875A27" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="8732fe3a-6cb0-4ad7-a835-ce246c29e63e" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="3019fac3-f9c8-4fb1-9ec6-d8ca7c09e6bf" 
/dev/sdb6: UUID="12f8c713-d70c-4d48-a2d2-ba43dd332415" TYPE="ext3" 
/dev/sdb7: UUID="8457453b-6b90-4f79-bbeb-530b4b497012" TYPE="ext3" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb7 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb6 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/ACER type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================== sda1/Boot: ==================================

totalt 3640
drwxrwxrwx 1 root root    4096 2008-05-27 03:07 .
drwxrwxrwx 1 root root    8192 2008-07-26 06:38 ..
-rwxrwxrwx 1 root root  262144 2008-08-16 06:01 bcd
-rwxrwxrwx 1 root root    9216 2008-08-16 06:01 bcd.LOG
-rwxrwxrwx 2 root root  262144 2007-01-17 00:05 bcd.LOG1
-rwxrwxrwx 2 root root       0 2007-01-16 23:52 bcd.LOG2
-rwxrwxrwx 1 root root    1024 2006-09-18 05:27 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2006-09-18 05:45 boot.sdi
-rwxrwxrwx 1 root root    2048 2006-09-18 05:27 etfsboot.com
drwxrwxrwx 1 root root       0 2008-05-27 03:07 fonts

================================== sda2/Boot: ==================================

totalt 988
drwxrwxrwx 1 root root   4096 2008-04-21 21:11 .
drwxrwxrwx 1 root root   8192 2009-01-05 19:37 ..
-rwxrwxrwx 1 root root 262144 2009-01-05 20:08 BCD
-rwxrwxrwx 1 root root 262144 2009-01-05 20:08 BCD.LOG
-rwxrwxrwx 1 root root  65536 2008-04-21 21:11 bootstat.dat
drwxrwxrwx 1 root root      0 2008-04-21 21:11 cs-CZ
drwxrwxrwx 1 root root      0 2008-04-21 21:11 da-DK
drwxrwxrwx 1 root root      0 2008-04-21 21:11 de-DE
drwxrwxrwx 1 root root      0 2008-04-21 21:11 el-GR
drwxrwxrwx 1 root root      0 2008-04-21 21:11 en-US
drwxrwxrwx 1 root root      0 2008-04-21 21:11 es-ES
drwxrwxrwx 1 root root      0 2008-04-21 21:11 fi-FI
drwxrwxrwx 1 root root      0 2008-04-21 21:11 Fonts
drwxrwxrwx 1 root root      0 2008-04-21 21:11 fr-FR
drwxrwxrwx 1 root root      0 2008-04-21 21:11 hu-HU
drwxrwxrwx 1 root root      0 2008-04-21 21:11 it-IT
drwxrwxrwx 1 root root      0 2008-04-21 21:11 ja-JP
drwxrwxrwx 1 root root      0 2008-04-21 21:11 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-21 02:23 memtest.exe
drwxrwxrwx 1 root root      0 2008-04-21 21:11 nb-NO
drwxrwxrwx 1 root root      0 2008-04-21 21:11 nl-NL
drwxrwxrwx 1 root root      0 2008-04-21 21:11 pl-PL
drwxrwxrwx 1 root root      0 2008-04-21 21:11 pt-BR
drwxrwxrwx 1 root root      0 2008-04-21 21:11 pt-PT
drwxrwxrwx 1 root root      0 2008-04-21 21:11 ru-RU
drwxrwxrwx 1 root root      0 2008-04-21 21:11 sv-SE
drwxrwxrwx 1 root root      0 2008-04-21 21:11 tr-TR
drwxrwxrwx 1 root root      0 2008-04-21 21:11 zh-CN
drwxrwxrwx 1 root root      0 2008-04-21 21:11 zh-HK
drwxrwxrwx 1 root root      0 2008-04-21 21:11 zh-TW

================================ sda4/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768

============================= sdb1/grub/menu.lst: =============================

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
# kopt=root=UUID=12f8c713-d70c-4d48-a2d2-ba43dd332415 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8732fe3a-6cb0-4ad7-a835-ce246c29e63e

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
uuid		8732fe3a-6cb0-4ad7-a835-ce246c29e63e
kernel		/vmlinuz-2.6.27-7-generic root=UUID=12f8c713-d70c-4d48-a2d2-ba43dd332415 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8732fe3a-6cb0-4ad7-a835-ce246c29e63e
kernel		/vmlinuz-2.6.27-7-generic root=UUID=12f8c713-d70c-4d48-a2d2-ba43dd332415 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8732fe3a-6cb0-4ad7-a835-ce246c29e63e
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Embedded
root		(hd0,3)
savedefault
chainloader	+1


================================== sdb1/grub: ==================================

totalt 216
drwxr-xr-x 2 root root   4096 2009-01-02 19:12 .
drwxr-xr-x 4 root root   4096 2009-01-02 19:12 ..
-rw-r--r-- 1 root root    197 2009-01-02 19:12 default
-rw-r--r-- 1 root root     30 2009-01-02 19:12 device.map
-rw-r--r-- 1 root root   8108 2009-01-02 19:12 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-02 19:12 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-02 19:12 installed-version
-rw-r--r-- 1 root root   8712 2009-01-02 19:12 jfs_stage1_5
-rw-r--r-- 1 root root   4927 2009-01-02 19:12 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-02 19:12 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-02 19:12 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-02 19:12 stage1
-rw-r--r-- 1 root root 121460 2009-01-02 19:12 stage2
-rw-r--r-- 1 root root   9556 2009-01-02 19:12 xfs_stage1_5

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc6
UUID=12f8c713-d70c-4d48-a2d2-ba43dd332415 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=8732fe3a-6cb0-4ad7-a835-ce246c29e63e /boot           ext3    relatime        0       2
# /dev/sdc7
UUID=8457453b-6b90-4f79-bbeb-530b4b497012 /home           ext3    relatime        0       2
# /dev/sdc5
UUID=3019fac3-f9c8-4fb1-9ec6-d8ca7c09e6bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb6/boot: ==================================

totalt 8
drwxr-xr-x  2 root root 4096 2009-01-02 18:54 .
drwxr-xr-x 20 root root 4096 2009-01-02 19:12 ..

=============================== StdErr Messages: ===============================

No errors were reported.

```

Acer Aspire 5920G
Intel Core 2 Duo processor T5550
Up to 1535MB NVIDIA GeForce 8600M GS TurboCache
4GB RAM
320GB HDD

And my 1TB external USB drive (where i try to install ubuntu):
Fujitsu Siemens Storagebird 35EV821

---

### Post by Pumalite on 2009-01-06
Edit menu.lst and try one of these two for 8.10:

/dev/sdb6: UUID="12f8c713-d70c-4d48-a2d2-ba43dd332415" TYPE="ext3" 
/dev/sdb7: UUID="8457453b-6b90-4f79-bbeb-530b4b497012" TYPE="ext3" 

My impresion is that you might have to reinstall.

---

### Post by pontuz2 on 2009-01-06
YES! I discovered just that in the Super Grub Disk each time i clicked something, the CD/DVD drive started making noise. I did just have to wait until the noise was over and then continue. I was too fast going trough the menues :D

Well, i tried to fix the GRUB but stille the same problem showes up. When i try to boot the linux kernel directly from SGD it doesnt work. I don't remeber what causes it. But thank you for the help so far and i will continue try fixing the GRUB!

One thing. If you look at my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc6
UUID=12f8c713-d70c-4d48-a2d2-ba43dd332415 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=8732fe3a-6cb0-4ad7-a835-ce246c29e63e /boot           ext3    relatime        0       2
# /dev/sdc7
UUID=8457453b-6b90-4f79-bbeb-530b4b497012 /home           ext3    relatime        0       2
# /dev/sdc5
UUID=3019fac3-f9c8-4fb1-9ec6-d8ca7c09e6bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Every partition on the external is set as sdc!
Shouldn't it be sdb?
If you look here:
```
fdisk -lu /dev/sdb:

Disk /dev/sdb: 1000,2 GB, 1000204886016 byte
255 huvuden, 63 sektorer/spår, 121601 cylindrar, totalt 1953525168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Diskidentifierare: 0x000d290e

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1   *          63     3903794     1951866   83  Linux
/dev/sdb2         3903795    50781464    23438835    5  Utökad
/dev/sdb5         3903858     7807589     1951866   82  Linux växling / Solaris
/dev/sdb6         7807653    27342629     9767488+  83  Linux
/dev/sdb7        27342693    50781464    11719386   83  Linux

```

Maby i'm totally wrong...

---

### Post by Pumalite on 2009-01-06
I think you got it. Edit /etc/fstab and make sure you have the right UUID's. But make sure you are editing the right fstab.

---

