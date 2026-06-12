---
title: "Grub stage 1.5read error"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by pontuz2 on 2009-01-05
Hi! I'm trying to install Ubuntu 8.10 on an 1TB external USB drive.
My computer is an Acer Aspire 5920 laptop and because it already got 4 primary partitions i decided to make it this way. The whole USB drive to ubuntu.

Well, everything went well in the installation and i installed GRUB to the first partition on the USB drive so it won't mess with Vistas MBR (when it's not inplugged).

I restarted the computer with the USB drive inplugged and GRUB showed perfectly and i was able to login to Ubuntu. The second time i booted my computer, GRUB show "GRUB GRUB stage 1.5read error" and i couldn't do anything else than reboot.
I've reinstalled it 3-4 times with no luck.. but can still boot Vista normally with the USB drive unplugged.

Oh yes, I've tried this (whith Live CD):
grub> sudo find /boot/grub/stage1
grub> root (hdx,y)
grub> setup (hdx)

...but the same error showes up.

Can i do something with the Super Grub Disk or do you have any other ideas.

	
Very grateful for help!
PS. Sorry for my bad english!

---

### Post by caljohnsmith on 2009-01-05
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by pontuz2 on 2009-01-05
Sorry, I have not got internet access in Live CD. I've downloaded the script from another PC but how do i import the file directly from the computer...

---

### Post by pontuz2 on 2009-01-05
Ahhh, my bad. I've got it:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1C6ACCCBE49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="4EC8E1278406103C" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="1CD1630028EEDA4B" TYPE="ntfs" 
/dev/sda4: UUID="666C87906C875A27" TYPE="ntfs" 
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
drwxrwxrwx 1 root root   8192 2009-01-05 19:07 ..
-rwxrwxrwx 1 root root 262144 2009-01-05 19:08 BCD
-rwxrwxrwx 1 root root 262144 2009-01-05 18:17 BCD.LOG
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

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by caljohnsmith on 2009-01-05
Thanks for posting that, pontuz2, but the script was not able to detect your Ubuntu USB drive; the script only found your Vista drive. Did you have the Ubuntu USB drive connected (and turned on) when you ran the script? In a terminal, if you do:
```
sudo fdisk -lu
```
You should be able to see the USB drive. If not, there probably is a hardware/BIOS issue. If you can see the USB drive though, how about rerunning the script again and posting the output. We can work from there.

---

### Post by pontuz2 on 2009-01-05
Yep, something strange happend. Now the fdisk -lu shows the external and here is the new output:

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

Something may be in swedish..

---

### Post by caljohnsmith on 2009-01-05
As expected, it looks like you have Grub correctly installed to your 1 TB drive, so I think your Grub problem is most likely due to how the 1 TB drive is configured in BIOS. Can you go into your BIOS and let me know what HDD-related settings you have for the 1 TB drive? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Please let me know what you find.

---

### Post by pontuz2 on 2009-01-05
I didn't find any sensible. It's got 5 menues, Information - Main - Security - Boot - Exit.

But here are some pictures:

MAIN
[http://rapidfiles.net/images/3782211.jpg](http://rapidfiles.net/images/3782211.jpg)

INFORMATION
[http://rapidfiles.net/images/6818422.jpg](http://rapidfiles.net/images/6818422.jpg)

BOOT
[http://rapidfiles.net/images/3232233.jpg](http://rapidfiles.net/images/3232233.jpg)

Hope you can read it.

---

### Post by caljohnsmith on 2009-01-05
I was afraid you wouldn't have any BIOS settings for your USB drive, and it looks like that is the case. How about trying this:
```
sudo grub
grub> root (hd1,0)
grub> install /grub/stage1 (hd1) /grub/stage2 p /grub/menu.lst
grub> quit

```
That will install Grub to the MBR of your USB drive, but it omits installing the stage1.5 file so that Grub points directly to the stage2 file in your sdb1 boot partition. It's a bit of a long shot, but sometimes that technique has worked in the past for some difficult Grub errors. If the commands complete successfully, reboot, and let me know what happens. We can go from there.

---

### Post by pontuz2 on 2009-01-05
Ok, i ran it and it didn't give any "success" message, just the text i just typed in and then a grub> prompt again.
So i rebooted and it just shows a blinking "_" in the upper left corner. Is there something else to do?

---

### Post by caljohnsmith on 2009-01-05
It sounds like Grub installed correctly, but once again Grub failed to boot on start up. You mentioned in your first post about the Super Grub Disk; have you tried using that to boot the USB drive, and does that give you any different results? Also, how about using the Super Grub Disk to reinstall Grub to the USB drive, because sometimes using a slightly different version of Grub can make a difference with unpredictable Grub errors like you are getting. You also might want to check the manufacturer's website for your motherboard and see if there is a BIOS upgrade available, because that might resolve your problem. Good luck and keep me posted about what you find and whether the Super Grub Disk helps at all.

---

### Post by pontuz2 on 2009-01-05
Thank you for your advices! I will try Super Grub Disk.

---

### Post by pontuz2 on 2009-01-06
Okey, I've got a stange problem here too..

When i boot from the Super Grub Disk Cdrom everything is okay, but when i am in the GNU/Linux menu (Fix Boot of Gnu/Linux (GRUB), Boot Gnu/Linux, Boot Gnu/Linux Directly, Gnu/Linux (Advanced))
and select something it just flashes a blue menu and then it stands "selectfile XXX" where X is some path to some file.

---

