---
title: "installer added listing for ubuntu &amp; xp, but need to add vista"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by Hansmc on 2008-12-31
Computer had Vista. Installed xp and then Ubuntu. Ubuntu added grub listing for one windows system but not the other.

Here is fdisk output

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1317        7690    51199155    7  HPFS/NTFS
/dev/sda4            7691       38913   250798747+   5  Extended
/dev/sda5            7691        9602    15358108+   7  HPFS/NTFS
/dev/sda6            9603       12152    20482843+  83  Linux
/dev/sda7           12153       12789     5116671   82  Linux swap / Solaris
/dev/sda8           12790       38913   209840998+   b  W95 FAT32

```

sda3 has vista on it.
sda5 has xp on it.
[SIZE="3"][SIZE="5"][/SIZE][/SIZE]I double checked. You will see why.

Here is the one menu.lst entry.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

That boots to xp. !? Hows that? It is pointing to the partition with vista on it. If I change to (hd0,4), that does not boot to anything. Thanks for your help.

---

### Post by caljohnsmith on 2008-12-31
Probably what happened is you installed XP after Vista? If that's true, it would explain why you boot into XP when you boot Vista's partition, because XP would have put its boot files in the Vista partition and rewrote the boot sector to boot XP's "ntldr" rather than Vista's "bootmgr". But in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Hansmc on 2008-12-31
Here is the out put. Thanks

```


============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 161792.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 21141540.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       swap

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2          161792    21133311    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *    21141540   123539849    51199155    7  HPFS/NTFS
/dev/sda4       123539850   625137344   250798747+   5  Extended
/dev/sda5       123539913   154256129    15358108+   7  HPFS/NTFS
/dev/sda6       154256193   195221879    20482843+  83  Linux
/dev/sda7       195221943   205455284     5116671   82  Linux swap / Solaris
/dev/sda8       205455348   625137344   209840998+   b  W95 FAT32

sfdisk -V /dev/sda:

Warning: partition 2 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0C0C" TYPE="vfat" 
/dev/sda2: UUID="38141A44141A0592" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="5AF81D70F81D4B9F" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="78908A76908A3AA0" TYPE="ntfs" 
/dev/sda6: LABEL="UBUNTU" UUID="dfc02510-4cec-400b-886b-05db068cebb9" TYPE="ext3" 
/dev/sda7: UUID="11b3ee2a-ee3c-42f5-9619-02f18a050cff" TYPE="swap" 
/dev/sda8: LABEL="DOCS" UUID="4952-C9AF" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/t2/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=t2)

================================ sda3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================== sda3/Boot: ==================================

total 784
drwxrwxrwx 1 root root   4096 2008-02-04 18:23 .
drwxrwxrwx 1 root root   8192 2008-12-26 01:31 ..
-rwxrwxrwx 1 root root  28672 2008-12-26 01:03 BCD
-rwxrwxrwx 2 root root  24576 2008-12-25 00:28 BCD.Backup.0001
-rwxrwxrwx 1 root root 262144 2008-12-25 10:43 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-02-04 18:23 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-02-04 18:23 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-02-04 18:23 bootstat.dat
drwxrwxrwx 1 root root      0 2008-02-04 18:23 cs-CZ
drwxrwxrwx 1 root root      0 2008-02-04 18:23 da-DK
drwxrwxrwx 1 root root      0 2008-02-04 18:23 de-DE
drwxrwxrwx 1 root root      0 2008-02-04 18:23 el-GR
drwxrwxrwx 1 root root      0 2008-02-04 18:23 en-US
drwxrwxrwx 1 root root      0 2008-02-04 18:23 es-ES
drwxrwxrwx 1 root root      0 2008-02-04 18:23 fi-FI
drwxrwxrwx 1 root root      0 2008-02-04 18:23 Fonts
drwxrwxrwx 1 root root      0 2008-02-04 18:23 fr-FR
drwxrwxrwx 1 root root      0 2008-02-04 18:23 hu-HU
drwxrwxrwx 1 root root      0 2008-02-04 18:23 it-IT
drwxrwxrwx 1 root root      0 2008-02-04 18:23 ja-JP
drwxrwxrwx 1 root root      0 2008-02-04 18:23 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-20 18:48 memtest.exe
drwxrwxrwx 1 root root      0 2008-02-04 18:23 nb-NO
drwxrwxrwx 1 root root      0 2008-02-04 18:23 nl-NL
drwxrwxrwx 1 root root      0 2008-02-04 18:23 pl-PL
drwxrwxrwx 1 root root      0 2008-02-04 18:23 pt-BR
drwxrwxrwx 1 root root      0 2008-02-04 18:23 pt-PT
drwxrwxrwx 1 root root      0 2008-02-04 18:23 ru-RU
drwxrwxrwx 1 root root      0 2008-02-04 18:23 sv-SE
drwxrwxrwx 1 root root      0 2008-02-04 18:23 tr-TR
drwxrwxrwx 1 root root      0 2008-02-04 18:23 zh-CN
drwxrwxrwx 1 root root      0 2008-02-04 18:23 zh-HK
drwxrwxrwx 1 root root      0 2008-02-04 18:23 zh-TW

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dfc02510-4cec-400b-886b-05db068cebb9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dfc02510-4cec-400b-886b-05db068cebb9

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
uuid		dfc02510-4cec-400b-886b-05db068cebb9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dfc02510-4cec-400b-886b-05db068cebb9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		dfc02510-4cec-400b-886b-05db068cebb9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dfc02510-4cec-400b-886b-05db068cebb9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dfc02510-4cec-400b-886b-05db068cebb9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dfc02510-4cec-400b-886b-05db068cebb9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dfc02510-4cec-400b-886b-05db068cebb9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dfc02510-4cec-400b-886b-05db068cebb9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dfc02510-4cec-400b-886b-05db068cebb9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3 (hd0,2)
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dfc02510-4cec-400b-886b-05db068cebb9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=11b3ee2a-ee3c-42f5-9619-02f18a050cff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda6/boot: ==================================

total 23796
drwxr-xr-x  3 root root    4096 2008-12-25 00:17 .
drwxr-xr-x 20 root root    4096 2008-12-25 00:16 ..
-rw-r--r--  1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 15:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 15:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-31 16:47 grub
-rw-r--r--  1 root root 8197037 2008-12-25 00:16 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8196738 2008-12-25 00:17 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 15:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 15:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 15:46 vmlinuz-2.6.27-9-generic

=============================== sda6/boot/grub: ===============================

total 244
drwxr-xr-x 3 root root   4096 2008-12-31 16:47 .
drwxr-xr-x 3 root root   4096 2008-12-25 00:17 ..
-rw-r--r-- 1 root root    197 2008-12-24 21:25 default
-rw-r--r-- 1 root root     15 2008-12-24 21:25 device.map
-rw-r--r-- 1 root root   8108 2008-12-24 21:25 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-24 21:25 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-24 21:25 installed-version
-rw-r--r-- 1 root root   8712 2008-12-24 21:25 jfs_stage1_5
-rw-r--r-- 1 root root   5105 2008-12-31 16:47 menu.lst
-rw-r--r-- 1 root root   5105 2008-12-31 16:44 menu.lst~
-rw-r--r-- 1 root root   5101 2008-12-31 16:17 menu.lst.backup
-rw-r--r-- 1 root root   5097 2008-12-31 16:23 menu.lst.old
-rw-r--r-- 1 root root   7352 2008-12-24 21:25 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-24 21:25 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-31 16:17 splashimages
-rw-r--r-- 1 root root    512 2008-12-24 21:25 stage1
-rw-r--r-- 1 root root 121460 2008-12-24 21:25 stage2
-rw-r--r-- 1 root root   9556 2008-12-24 21:25 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown BootLoader  on /dev/sda1

00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 9d 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  4b 73 02 00 80 00 29 0c  0c d8 07 44 65 6c 6c 55  |Ks....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.


```

---

### Post by caljohnsmith on 2008-12-31
OK, unfortunately it is like I suspected; XP overwrote your Vista's boot sector, and XP also put all its boot files in your Vista partition. To fix the problem, the first thing to do would be to boot your Vista Install CD, go to the command line and run:
```
bootrec /fixboot
```
And then when you choose Vista from your Grub menu, you should be able to boot into Vista. To boot into XP, you could add XP to your Vista boot menu using [EasyBCD]("http://neosmart.net/dl.php?id=1"). If you want to boot XP from Grub, you would have to move your XP boot files back to the sda5 XP partition and also repair the XP boot sector, but it can be done if you want to do it. Let me know first if you can boot into Vista OK, and also let me know what you want to do about booting XP. We can work from there if you want.

---

### Post by Hansmc on 2008-12-31
How do I get to the command line? Vista cd just starts installing vista.

I do want to boot to xp also.

---

### Post by caljohnsmith on 2008-12-31
OK, sounds like you have an OEM Vista CD, so that's why you can't get a command line. Instead, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the sda3 Windows Vista partition, choose "boot", then choose "Backup BS"; if testdisk gives you a warning that the sectors aren't identical, then choose "write". After you are done doing the "Backup BS" in testdisk, reboot and let me know exactly what happens when you boot Windows Vista from the Grub menu. We can work from there.

---

### Post by Hansmc on 2009-01-01
Got Vista up and going. On the second or third dialog box of the vista install it gives me the option to enter recovery mode, so that is how I did it. Thanks for your help caljohnsmith.

Now, how do I add the option to boot to xp. I would like to use grub.

---

### Post by caljohnsmith on 2009-01-01
OK, to boot XP from your Grub menu, the first thing to do would be to fix your XP sda5 partition's boot sector, because currently the boot sector shows the starting point of the sda5 partition as sector "63" when really the sda5 partition starts at sector 123539913 according to fdisk. To correct it, you can use testdisk:
```
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows XP sda5 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write".

Next you'll need to move your Win XP boot files from your Vista sda3 partition back to the XP sda5 partition:
```
sudo mkdir /mnt/sda3 /mnt/sda5
sudo mount /dev/sda3 /mnt/sda3
sudo mount /dev/sda5 /mnt/sda5
sudo mv /mnt/sda3/boot.ini /mnt/sda3/ntldr /mnt/sda3/NTDETECT.COM /mnt/sda5
```
Then modify your Grub's menu.lst to include an entry to boot XP:
```
gksudo gedit /boot/grub/menu.lst
```
And after the Vista entry add:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Reboot, let me know exactly what happens when you boot XP from your Grub menu, and we can work from there.

---

### Post by Hansmc on 2009-01-01
When I choose windows xp on the grub os list, it booted normally. I checked vista and ubuntu and they both work also.

The only trouble I had, was I had to force mount the two file systems (sda3, sda5). Other then that I followed your instructions and they worked fine. You are very thorough with your instructions. Thanks a lot.

---

