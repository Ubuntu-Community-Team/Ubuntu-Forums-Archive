---
title: "new 8.10 install grub error 21 problem"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by therob1 on 2008-12-16
ive tried looking up other threads and due to my serious lack of linux skill i can not fully understand what i need to do or how i need to get from A to B . 

i have/had a windows vista install with 2x1Tb drives in a motherboard raid 0 setup. I then had a spare sata 250gb drive that i chose to install ubuntu onto. when it rebooted after install it just booted to an error 21. I have tried changing boot orders and disabling drives in bios etc, but no luck. i now have 2 operating systems that just dont appear to do anything. i have managed to get some info from the live cd which im hoping will give someone an idea of what i need to change, and if i can do it from the live cd?

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1baf8410

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      243200  1953495040    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9b8b9b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29760   239047168+  83  Linux
/dev/sdc2           29761       30515     6064537+   5  Extended
/dev/sdc5           29761       30515     6064506   82  Linux swap / Solaris
root@ubuntu:/home/ubuntu#

---

### Post by caljohnsmith on 2008-12-16
Can you set your BIOS to boot the sdc drive on start up? If so, the solution to your problem could be really simple. If you can set your BIOS to boot the sdc drive, then you can install Grub to the MBR of sdc so that it is bootable, and you should be able to boot into Ubuntu without any more Grub errors. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
That will install Grub to the MBR of your sdc drive so that it is bootable, and then to restore a Windows MBR to your Vista drive, do:
```
sudo lilo -M  /dev/sda mbr
```
Then reboot, set your BIOS to boot the sdc drive, and you should get the Grub menu and be able to boot Ubuntu. See if you can get that far, and then I can help you boot Windows from the Grub menu. Let me know how it goes or if you run into problems.

---

### Post by therob1 on 2008-12-17
> **caljohnsmith said:**
> Can you set your BIOS to boot the sdc drive on start up? If so, the solution to your problem could be really simple. If you can do set your BIOS to boot the sdc drive, then you can install Grub to the MBR of sdc so that it is bootable, and you should be able to boot into Ubuntu without any more Grub errors. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
That will install Grub to the MBR of your sdc drive so that it is bootable, and then to restore a Windows MBR to your Vista drive, do:
```
sudo lilo -M  /dev/sda mbr
```
Then reboot, set your BIOS to boot the sdc drive, and you should get the Grub menu and be able to boot Ubuntu. See if you can get that far, and then I can help you boot Windows from the Grub menu. Let me know how it goes or if you run into problems.


your a genius, i got it working right away with your help.

thanks,

Rob.

---

### Post by caljohnsmith on 2008-12-17
Glad to hear that worked OK; if you need any further help booting Windows from your Grub menu, let me know. Otherwise cheers and have fun with Windows and Ubuntu. :)

---

### Post by mindas22 on 2008-12-29
I have installed ubuntu 8.10

sda and sdb > raid1 (promise tx2300)
sdc > windows vista, ubuntu, 
menu.lst
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Windows Vista/Longhorn (loader)
root (hd2,0)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


windows vista is in sdc5 partition, so i change to root(hd2,4)
anyway no luck here

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 6374 51199123+ 7 HPFS/NTFS
/dev/sdc2 6375 60800 437176845 f W95 Ext'd (LBA)
/dev/sdc5 6375 14023 61440561 7 HPFS/NTFS
/dev/sdc6 14024 17366 26852616 83 Linux
/dev/sdc7 17367 17847 3863601 82 Linux swap / Solaris
/dev/sdc8 17848 60800 345019941 7 HPFS/NTFS



ubuntu is booting no problem

Any advice?
Thank You!

---

### Post by caljohnsmith on 2008-12-29
Mindas22, in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by mindas22 on 2008-12-29
Results:
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #7 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on boot drive #-127 in 
    partition #1 for its boot files.
 => Grub is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /grldr /ntldr /NTDETECT.COM /Boot

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc7: _________________________________________________________________________

    File system:       swap

sdc8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0194101

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976639544   488319741    7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0194101

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976639544   488319741    7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90269026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sdc2       102398310   976751999   437176845    f  W95 Ext'd (LBA)
/dev/sdc5       102398373   225279494    61440561    7  HPFS/NTFS
/dev/sdc6       225279558   278984789    26852616   83  Linux
/dev/sdc7       278984853   286712054     3863601   82  Linux swap / Solaris
/dev/sdc8       286712118   976751999   345019941    7  HPFS/NTFS

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8820B4B720B4AE16" LABEL="RAID 1" TYPE="ntfs" 
/dev/sdb1: UUID="8820B4B720B4AE16" LABEL="RAID 1" TYPE="ntfs" 
/dev/sdc1: UUID="FCC85AE6C85A9F28" LABEL="system-xp" TYPE="ntfs" 
/dev/sdc5: UUID="FA948CE9948CA9A9" LABEL="vista" TYPE="ntfs" 
/dev/sdc6: UUID="83aa5870-d4c2-4410-a6f3-a0a4960ca583" TYPE="ext3" 
/dev/sdc7: UUID="ac09f2fe-c556-41e7-b92f-1db1a5d77e02" TYPE="swap" 
/dev/sdc8: UUID="4A7C81367C811DB7" LABEL="ivairus" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdc6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mind/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mind)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=mind)
/dev/sdb1 on /media/RAID 1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/RAID 1-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sdc1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


================================== sdc1/Boot: ==================================

total 524
drwxrwxrwx 1 root root   4096 2008-12-14 13:04 .
drwxrwxrwx 1 root root   8192 2008-12-29 13:36 ..
-rwxrwxrwx 1 root root  24576 2008-12-25 13:11 BCD
-rwxrwxrwx 1 root root  21504 2008-12-25 13:08 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-14 13:04 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-14 13:04 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-12-14 13:04 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-14 13:04 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-14 13:04 da-DK
drwxrwxrwx 1 root root      0 2008-12-14 13:04 de-DE
drwxrwxrwx 1 root root      0 2008-12-14 13:04 el-GR
drwxrwxrwx 1 root root      0 2008-12-14 13:04 en-US
drwxrwxrwx 1 root root      0 2008-12-14 13:04 es-ES
drwxrwxrwx 1 root root      0 2008-12-14 13:04 fi-FI
drwxrwxrwx 1 root root      0 2008-12-14 13:04 Fonts
drwxrwxrwx 1 root root      0 2008-12-14 13:04 fr-FR
drwxrwxrwx 1 root root      0 2008-12-14 13:04 hu-HU
drwxrwxrwx 1 root root      0 2008-12-14 13:04 it-IT
drwxrwxrwx 1 root root      0 2008-12-14 13:04 ja-JP
drwxrwxrwx 1 root root      0 2008-12-14 13:04 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-21 02:47 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-14 13:04 nb-NO
drwxrwxrwx 1 root root      0 2008-12-14 13:04 nl-NL
drwxrwxrwx 1 root root      0 2008-12-14 13:04 pl-PL
drwxrwxrwx 1 root root      0 2008-12-14 13:04 pt-BR
drwxrwxrwx 1 root root      0 2008-12-14 13:04 pt-PT
drwxrwxrwx 1 root root      0 2008-12-14 13:04 ru-RU
drwxrwxrwx 1 root root      0 2008-12-14 13:04 sv-SE
drwxrwxrwx 1 root root      0 2008-12-14 13:04 tr-TR
drwxrwxrwx 1 root root      0 2008-12-14 13:04 zh-CN
drwxrwxrwx 1 root root      0 2008-12-14 13:04 zh-HK
drwxrwxrwx 1 root root      0 2008-12-14 13:04 zh-TW

=========================== sdc6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=83aa5870-d4c2-4410-a6f3-a0a4960ca583 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=83aa5870-d4c2-4410-a6f3-a0a4960ca583

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
uuid		83aa5870-d4c2-4410-a6f3-a0a4960ca583
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=83aa5870-d4c2-4410-a6f3-a0a4960ca583 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		83aa5870-d4c2-4410-a6f3-a0a4960ca583
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=83aa5870-d4c2-4410-a6f3-a0a4960ca583 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		83aa5870-d4c2-4410-a6f3-a0a4960ca583
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=83aa5870-d4c2-4410-a6f3-a0a4960ca583 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		83aa5870-d4c2-4410-a6f3-a0a4960ca583
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=83aa5870-d4c2-4410-a6f3-a0a4960ca583 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		83aa5870-d4c2-4410-a6f3-a0a4960ca583
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista/Longhorn (loader)
root		(hd2,4)
savedefault
map (0x82) (0x80) 
map (0x80) (0x82)
makeactive
#map		(hd0) (hd2)
#map		(hd2) (hd0)
chainloader	+1


=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc6
UUID=83aa5870-d4c2-4410-a6f3-a0a4960ca583 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc7
UUID=ac09f2fe-c556-41e7-b92f-1db1a5d77e02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc6/boot: ==================================

total 24188
drwxr-xr-x  3 root root    4096 2008-12-29 14:29 .
drwxr-xr-x 20 root root    4096 2008-12-26 04:42 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-29 22:09 grub
-rw-r--r--  1 root root 8194870 2008-12-26 04:42 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8599948 2008-12-29 14:29 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sdc6/boot/grub: ===============================

total 228
drwxr-xr-x 3 root root   4096 2008-12-29 22:09 .
drwxr-xr-x 3 root root   4096 2008-12-29 14:29 ..
-rw-r--r-- 1 root root    197 2008-12-26 04:21 default
-rw-r--r-- 1 root root     45 2008-12-26 04:21 device.map
-rw-r--r-- 1 root root   8108 2008-12-26 04:21 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-26 04:21 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-26 04:21 installed-version
-rw-r--r-- 1 root root   8712 2008-12-26 04:21 jfs_stage1_5
-rw-r--r-- 1 root root   5170 2008-12-29 22:09 menu.lst
-rw-r--r-- 1 root root   5040 2008-12-26 04:42 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-26 04:21 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-26 04:21 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-29 02:44 splashimages
-rw-r--r-- 1 root root    512 2008-12-26 04:21 stage1
-rw-r--r-- 1 root root 121460 2008-12-26 04:21 stage2
-rw-r--r-- 1 root root   9556 2008-12-26 04:21 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2008-12-29
Since it's not entirely clear which drive you are booting on start up, how about trying this to boot Vista:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
That should work if you are booting the sdc Ubuntu drive on start up; your Vista boot files are actually in sdc1 since you installed Vista to sdc5, a logical partition, so you need to boot sdc1, not sdc5. Let me know exactly what happens when you try the above entry from the Grub menu, and we can work from there.

---

### Post by mindas22 on 2008-12-29
Thats it!
Thank You very much caljohnsmith 

> **caljohnsmith said:**
> Since it's not entirely clear which drive you are booting on start up, how about trying this to boot Vista:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
That should work if you are booting the sdc Ubuntu drive on start up; your Vista boot files are actually in sdc1 since you installed Vista to sdc5, a logical partition, so you need to boot sdc1, not sdc5. Let me know exactly what happens when you try the above entry from the Grub menu, and we can work from there.

---

### Post by caljohnsmith on 2008-12-29
> **mindas22 said:**
> Thats it!
Thank You very much caljohnsmith
You're welcome, glad that worked OK; cheers and have fun with Vista and Ubuntu.

---

### Post by getbighugeair on 2009-01-15
I ran the script that shows all the volume info and grub location and am having issues with Grub error 21 as well.

Please let me know from my setup - 1 80G SATA with Windows XP on it and 2 160G mirrored SATAs with 2 unrelated IDE drives (82G each) with Ubuntu installed in a partition on the last drive.  Following the previous example I was unable to make sense out of the naming convention in HD2, 0 in the grub utility.

The file below is showing the volume info
##################3
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #5 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sde2: _________________________________________________________________________

    File system:       Extended Partition

sde5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb372b372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48e5f277

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48e5f277

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   312576704   156288321    7  HPFS/NTFS

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe755e755

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   160810649    80405293+   7  HPFS/NTFS

sfdisk -V /dev/sdd:

/dev/sdd: OK

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

Disk /dev/sde: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x052bde90

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   154786274    77393106   83  Linux
/dev/sde2       154786275   160826714     3020220    5  Extended
/dev/sde5       154786338   160826714     3020188+  82  Linux swap / Solaris

sfdisk -V /dev/sde:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sde: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="FA6CDF7E6CDF345B" TYPE="ntfs" 
/dev/sdb1: UUID="4EA077AEA0779B63" LABEL="Data" TYPE="ntfs" 
/dev/sdc1: UUID="4EA077AEA0779B63" LABEL="Data" TYPE="ntfs" 
/dev/sdd1: UUID="D88C85768C854FC4" TYPE="ntfs" 
/dev/sde1: UUID="bddfe404-4619-4856-929b-18eae08e112d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sde5: UUID="bd782968-502f-4bcb-873a-3409a31b0d6e" TYPE="swap" 
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

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


================================ sdd1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


=========================== sde1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=bddfe404-4619-4856-929b-18eae08e112d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bddfe404-4619-4856-929b-18eae08e112d

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
uuid		bddfe404-4619-4856-929b-18eae08e112d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bddfe404-4619-4856-929b-18eae08e112d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		bddfe404-4619-4856-929b-18eae08e112d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bddfe404-4619-4856-929b-18eae08e112d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		bddfe404-4619-4856-929b-18eae08e112d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=bddfe404-4619-4856-929b-18eae08e112d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=bd782968-502f-4bcb-873a-3409a31b0d6e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sde1/boot: ==================================

total 11940
drwxr-xr-x  3 root root    4096 2009-01-16 02:44 .
drwxr-xr-x 20 root root    4096 2009-01-16 02:44 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-16 02:44 grub
-rw-r--r--  1 root root 8168018 2009-01-16 02:44 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sde1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-16 02:44 .
drwxr-xr-x 3 root root   4096 2009-01-16 02:44 ..
-rw-r--r-- 1 root root    197 2009-01-16 02:44 default
-rw-r--r-- 1 root root     75 2009-01-16 02:44 device.map
-rw-r--r-- 1 root root   8108 2009-01-16 02:44 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-16 02:44 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-16 02:44 installed-version
-rw-r--r-- 1 root root   8712 2009-01-16 02:44 jfs_stage1_5
-rw-r--r-- 1 root root   4841 2009-01-16 02:44 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-16 02:44 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-16 02:44 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-16 02:44 stage1
-rw-r--r-- 1 root root 121460 2009-01-16 02:44 stage2
-rw-r--r-- 1 root root   9556 2009-01-16 02:44 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
###################################

Any help is appreciated.

---

### Post by caljohnsmith on 2009-01-16
So are you getting the Grub error 21 before seeing a Grub menu? If so, I think the best solution would be to install Grub to your Ubuntu sde drive, but to make that work you will need to change your BIOS to boot the Ubuntu sde drive--can you do that? If you can, how about doing:
```
sudo grub
grub> device (hd0) /dev/sde
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
```
Then reboot, set your BIOS to boot the Ubuntu drive, and let me know exactly what happens. We can work from there.

---

### Post by getbighugeair on 2009-01-16
Thank you for the help.  Now Ubuntu boots and I get to the boot select screen for the OS.  Ubuntu boots from the first selection in generic mode, but I have 2 Windows selections and neither one works.  Now what ?  I would really like to understand this all after it works (after getting dual boot to work)

On a side note, I am using an Nvidia HW RAID controller on the Mobo and Ubuntu is seeing each drive as a separate drive.

Thanks

---

### Post by caljohnsmith on 2009-01-16
OK, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace the two Windows entries at the end of the file with:
```
title Microsoft Windows XP Professional (hd1)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Microsoft Windows XP Professional (hd2)
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
Reboot, try each of the above entries from your Grub menu, and let me know exactly what happens. Most likely one will work, but if not, we can go from there.

---

### Post by getbighugeair on 2009-01-16
Thanks again.  The second entry worked fine.  Can I delete the first entry so it is off the list seeing as it the wrong drive I am guessing yes.

Second, my 160G drive is actually an Nvidia RAID mirror array and not 2 drives.  I have not even mounted one of the drives in Ubuntu for fear of screwing up the RAID.

Any recommendations for how to get Ubuntu to see the drive as 1 logical volume not 2 HW volumes ?

Thanks again for the simplicity of your fix.

---

### Post by caljohnsmith on 2009-01-16
Glad to hear one of those entries worked OK, and yes, you can delete the other one. About your RAID mirror, I don't have much experience with RAID, but if I were you I would install "mdadm" and check the documentation. I believe that's the package that will allow you to set up your RAID mirror correctly in Ubuntu. Good luck and let me know how it goes. :)

---

