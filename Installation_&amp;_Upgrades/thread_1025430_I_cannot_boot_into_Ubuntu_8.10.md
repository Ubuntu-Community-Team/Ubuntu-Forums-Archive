---
title: "I cannot boot into Ubuntu 8.10"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by ahmed_nasr on 2008-12-30
Hi there people ,

I am trying to install ubuntu 8.10 alongside with windows XP . I did install it actually twice , but each time after installation , the system reboots to XP , I never get the choice between XP and 8.10 , so what can I do ?

---

### Post by TomasJancik on 2008-12-30
don't you have two disks and install ubuntu (and grub) on the second one?

---

### Post by ramon457 on 2008-12-30
should have used the wubi installer it gives you a choice between ubuntu and xp

---

### Post by ahmed_nasr on 2008-12-30
> **TomasJancik said:**
> don't you have two disks and install ubuntu (and grub) on the second one?

no am using same hard drive for XP and Ubuntu , this could work , couldn't it ?

---

### Post by ahmed_nasr on 2008-12-30
> **ramon457 said:**
> should have used the wubi installer it gives you a choice between ubuntu and xp

I tried the inside windows installation and the regular one , both give same problem

---

### Post by EV500B on 2008-12-30
So... huh! try to install [smart boot manager]("http://btmgr.sourceforge.net/") into a floppy disk and then boot from it
(Don't forget to set your bios so as it boots from the floppy at first)
Then you'll see an interface and guess/choose where you've install ubuntu

hint: It's probably a Linux filesystem(marked as linux at the right) or maybe the first partition of any of your drives.

then press Enter and this should boot (Let's hope)

---

### Post by caljohnsmith on 2008-12-30
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by ahmed_nasr on 2008-12-30
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

that's what i got in the shell :```



--2008-12-30 20:25:27--  http://home.comcast.net/~ubuntu_grub/boot_info_script.txt
Resolving home.comcast.net... failed: Name or service not known.
wget: unable to resolve host address `home.comcast.net'

```


I noticed too that no webpages open on the live cd ... i mean there's an internet connection icon but the pages do not load ... which is another problem that I cannot interpret .... plz help me guys here

---

### Post by caljohnsmith on 2008-12-30
Can you download that script from some other computer, and then transfer it to your Live CD desktop? Maybe using a floppy or better yet, a USB stick? It would sure help for troubleshooting. If you right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser and choose "save link as", you should be able to save it and hopefully transfer it to your Ubuntu desktop. If you can get the "boot_info_script.txt" on your Ubuntu desktop, just run it with:
```
sudo bash ~/Desktop/boot*.txt
```
Let me know how that goes.

---

### Post by ahmed_nasr on 2008-12-30
> **caljohnsmith said:**
> Can you download that script from some other computer, and then transfer it to your Live CD desktop? Maybe using a floppy or better yet, a USB stick? It would sure help for troubleshooting. If you right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser and choose "save link as", you should be able to save it and hopefully transfer it to your Ubuntu desktop. If you can get the "boot_info_script.txt" on your Ubuntu desktop, just run it with:
```
sudo bash ~/Desktop/boot*.txt
```
Let me know how that goes.

There you go , the contents of Results.txt :

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #9 for its boot files.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb10: _________________________________________________________________________

    File system:       swap

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sdb9 and 
                       looks at sector 475888581 of the same hard drive for 
                       the stage2 file (a stage2 file is at this location on 
                       /dev/sdb) and on partition #9 for menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a800a7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   625137344   312560640    f  W95 Ext'd (LBA)
/dev/sda5           16128   307227059   153605466    7  HPFS/NTFS
/dev/sda6       307227123   625137344   158955111    7  HPFS/NTFS

sfdisk -V /dev/sda:

partition [6]: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3fd93fd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sdb2        61432560   488392064   213479752+   f  W95 Ext'd (LBA)
/dev/sdb5        61432623   163830869    51199123+   7  HPFS/NTFS
/dev/sdb6       163830933   266229179    51199123+   7  HPFS/NTFS
/dev/sdb7       266229243   368627489    51199123+   7  HPFS/NTFS
/dev/sdb8       368627553   467909189    49640818+   7  HPFS/NTFS
/dev/sdb9       467909253   486335744     9213246   83  Linux
/dev/sdb10      486335808   488392064     1028128+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 7: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 8: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 9: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 10: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 8027 MB, 8027897856 bytes
14 heads, 22 sectors/track, 50907 cylinders, total 15679488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2232    15679487     7838628    b  W95 FAT32

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="F638AB8038AB3E8D" LABEL="games2" TYPE="ntfs" 
/dev/sda6: UUID="B0FCD107FCD0C92C" LABEL="movies" TYPE="ntfs" 
/dev/sdb1: UUID="18786E35786E1234" TYPE="ntfs" 
/dev/sdb5: UUID="BAB8DE1FB8DDDA49" LABEL="downloads" TYPE="ntfs" 
/dev/sdb6: UUID="7634D88B34D84FAB" LABEL="Songs & movies" TYPE="ntfs" 
/dev/sdb7: UUID="F2E4ED51E4ED191D" LABEL="Games" TYPE="ntfs" 
/dev/sdb8: UUID="46ECD03EECD029C7" TYPE="ntfs" 
/dev/sdb9: UUID="56e0d347-9043-4abc-a7bd-c8cc19a2acd7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb10: UUID="ac7b83d1-8548-40f2-b3c6-2088105531cd" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="KINGSTON" UUID="3433-3231" TYPE="vfat" 

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
/dev/sdc1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="1" 1


=========================== sdb9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=56e0d347-9043-4abc-a7bd-c8cc19a2acd7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=56e0d347-9043-4abc-a7bd-c8cc19a2acd7

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
uuid		56e0d347-9043-4abc-a7bd-c8cc19a2acd7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56e0d347-9043-4abc-a7bd-c8cc19a2acd7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		56e0d347-9043-4abc-a7bd-c8cc19a2acd7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56e0d347-9043-4abc-a7bd-c8cc19a2acd7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		56e0d347-9043-4abc-a7bd-c8cc19a2acd7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		1
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb9
UUID=56e0d347-9043-4abc-a7bd-c8cc19a2acd7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb10
UUID=ac7b83d1-8548-40f2-b3c6-2088105531cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb9/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2008-12-30 12:40 .
drwxr-xr-x 20 root root    4096 2008-12-30 12:39 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-30 12:40 grub
-rw-r--r--  1 root root 8177063 2008-12-30 12:39 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb9/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2008-12-30 12:40 .
drwxr-xr-x 3 root root   4096 2008-12-30 12:40 ..
-rw-r--r-- 1 root root    197 2008-12-30 12:40 default
-rw-r--r-- 1 root root     30 2008-12-30 12:40 device.map
-rw-r--r-- 1 root root   8108 2008-12-30 12:40 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-30 12:40 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-30 12:40 installed-version
-rw-r--r-- 1 root root   8712 2008-12-30 12:40 jfs_stage1_5
-rw-r--r-- 1 root root   4612 2008-12-30 12:40 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-30 12:40 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-30 12:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-30 12:40 stage1
-rw-r--r-- 1 root root 121460 2008-12-30 12:40 stage2
-rw-r--r-- 1 root root   9556 2008-12-30 12:40 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sdc

00000000  fa 33 c0 8e d0 bc 00 7c  8b f4 50 07 50 1f fb fc  |.3.....|..P.P...|
00000010  bf 00 06 b9 00 01 f2 a5  ea 1d 06 00 00 be b8 06  |................|
00000020  ac 3c 00 74 0e 56 bb 07  00 b4 0e cd 10 5e ea 20  |.<.t.V.......^. |
00000030  06 00 00 cd 18 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000b0  00 00 00 00 00 00 00 00  50 65 6e 20 44 72 69 76  |........Pen Driv|
000000c0  65 20 57 69 74 68 6f 75  74 20 4f 70 65 72 61 74  |e Without Operat|
000000d0  69 6e 67 20 53 79 73 74  65 6d 2e 52 65 6d 6f 76  |ing System.Remov|
000000e0  65 20 50 65 6e 20 44 72  69 76 65 20 41 6e 64 20  |e Pen Drive And |
000000f0  52 65 62 6f 6f 74 2e 20  00 00 00 00 00 00 00 00  |Reboot. ........|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  01 02 03 04 00 00 00 23  |...............#|
000001c0  1c 00 0b 0d d6 98 b8 08  00 00 48 37 ef 00 00 00  |..........H7....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.

```

---

### Post by ahmed_nasr on 2008-12-30
> **EV500B said:**
> So... huh! try to install [smart boot manager]("http://btmgr.sourceforge.net/") into a floppy disk and then boot from it
(Don't forget to set your bios so as it boots from the floppy at first)
Then you'll see an interface and guess/choose where you've install ubuntu

hint: It's probably a Linux filesystem(marked as linux at the right) or maybe the first partition of any of your drives.

then press Enter and this should boot (Let's hope)

what extension should I use ? there are exe ,rpm ,tar.gz , tgz .... ?

---

### Post by stderr on 2008-12-30
Well, from first glance, it would seem that you've installed the GRUB bootloader to a different drive to Windows, but you're still booting from the Windows drive.

Maybe simply entering your motherboard's BIOS and changing the boot device to your other hard drive will achieve what you want.

---

### Post by ahmed_nasr on 2008-12-30
> **stderr said:**
> Well, from first glance, it would seem that you've installed the GRUB bootloader to a different drive to Windows, but you're still booting from the Windows drive.

Maybe simply entering your motherboard's BIOS and changing the boot device to your other hard drive will achieve what you want.

Both XP and 8.10 are on the same drive ,the 250 GB one , anyway , I tried to boot from the other one as u suggested and to my surprise , I got grub loading but then an error 22 .... please can anybody eplain wht's going on , coz am not able to follow anymore ..

---

### Post by caljohnsmith on 2008-12-30
OK, first install Grub to the MBR (Master Boot Record) of your sdb drive:
```
sudo grub
grub> root (hd1,8)
grub> setup (hd1)
grub> quit
```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry at the bottom (where it begins with "title 1") to the following:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and you should get the Grub menu on start up if all goes well and be able to boot Windows or Ubuntu. Let me know how it goes or if you run into problems.

---

### Post by ahmed_nasr on 2008-12-30
> **caljohnsmith said:**
> OK, first install Grub to the MBR (Master Boot Record) of your sdb drive:
```
sudo grub
grub> root (hd1,8)
grub> setup (hd1)
grub> quit
```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry at the bottom (where it begins with "title 1") to the following:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and you should get the Grub menu on start up if all goes well and be able to boot Windows or Ubuntu. Let me know how it goes or if you run into problems.

the menu.lst opens an empty file , when i add the 3 lines in it and save , tells me that this file /boot/grub/menu.lst couldnt be found

---

### Post by caljohnsmith on 2008-12-30
My mistake, I forgot you were doing this from the Live CD, so instead try the following:
```
sudo mount /dev/sdb9 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```

---

### Post by ahmed_nasr on 2008-12-30
> **caljohnsmith said:**
> My mistake, I forgot you were doing this from the Live CD, so instead try the following:
```
sudo mount /dev/sdb9 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```

dude , you are the best , but u gotta tell me what all that means or where can i learn all that ....

that's enough for today :D ... but am still stuck with the internet problem .... that's tomorrow's thing .... good night my ubuntu friend

---

### Post by caljohnsmith on 2008-12-30
> **ahmed_nasr said:**
> dude , you are the best , but u gotta tell me what all that means or where can i learn all that ....

that's enough for today :D ... but am still stuck with the internet problem .... that's tomorrow's thing .... good night my ubuntu friend
Glad to hear that worked OK and you can now dual boot. If you want to learn more about Grub and booting issues, here's a few good resources:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Anyway, cheers and good luck getting your internet working too. :)

---

