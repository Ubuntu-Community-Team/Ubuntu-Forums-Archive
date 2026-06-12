---
title: "Dell d600 grub error 17 duel boot"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by lincoln32 on 2009-08-20
Dell d600 1.6 pentium mobil  bios a16 2gb ram 160gb hard drive win xp and ubuntu 9.04 grub fails error 17 after 10 trys I finally removed and installed in second laptop and all installed ok so what in the bios could be stopping grub?
160gb hard drive 
hda1 ntfs 97.65gib 27.65bib used /win xp pro
hda3 ext4 39.60gib  812.57 used /home
hda4 ext4 9.84 gib  2.14 used  /
hda2 extended 1.95
hda5 linux swap 1.95

---

### Post by presence1960 on 2009-08-20
GRUB error 17 has nothing to do with BIOS. Here is the explanation from GRUB manual -
 ```
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 
```

See [GRUB Manual page of errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors")

Why don't you boot off the Ubuntu Live Cd & choose "try ubuntu without any changes". When the desktop loads come back here and use the link in my signature line to download to desktop the Boot Info Script 0.32

Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on desktop. paste the entire contents of that file back here. Once pasted here highlight all text and click # sign on the toolbar to place code tags around the text. This info will show us your setup and boot process.

---

### Post by lincoln32 on 2009-08-20
I assumed that because grub and ubuntu works in the other laptop it was a bios concern but txt is here but I cannot read it so thanks for the help in advance






=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e2f74

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         308,480,130   312,576,704     4,096,575   5 Extended
/dev/sda5         308,480,193   312,576,704     4,096,512  82 Linux swap / Solaris
/dev/sda3         204,796,620   287,836,604    83,039,985  83 Linux
/dev/sda4         287,836,605   308,480,129    20,643,525  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B254A6E554A6AB93" TYPE="ntfs" 
/dev/sda3: UUID="5366604b-6396-439b-9a26-9cf17ab10cdc" TYPE="ext4" 
/dev/sda4: UUID="7490b096-d371-450a-9061-5a51838c2101" TYPE="ext4" 
/dev/sda5: UUID="0bef4ec6-f83e-45bf-8403-4d0ba82a7f7e" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7490b096-d371-450a-9061-5a51838c2101 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7490b096-d371-450a-9061-5a51838c2101

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7490b096-d371-450a-9061-5a51838c2101
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7490b096-d371-450a-9061-5a51838c2101 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7490b096-d371-450a-9061-5a51838c2101
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7490b096-d371-450a-9061-5a51838c2101 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7490b096-d371-450a-9061-5a51838c2101
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=7490b096-d371-450a-9061-5a51838c2101 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=5366604b-6396-439b-9a26-9cf17ab10cdc /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=0bef4ec6-f83e-45bf-8403-4d0ba82a7f7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 149.2GB: boot/grub/menu.lst
 149.1GB: boot/grub/stage2
 149.1GB: boot/initrd.img-2.6.28-11-generic
 149.2GB: boot/vmlinuz-2.6.28-11-generic
 149.1GB: initrd.img
 149.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  e1 7f 12 00 00 00 00 00  82 3c 10 00 82 3c 10 00  |.........<...<..|
00000010  cb 01 00 00 0a 00 00 00  eb 7f 12 00 00 00 00 00  |................|
00000020  40 9f 11 00 97 3c 10 00  cc 01 00 00 0a 00 00 00  |@....<..........|
00000030  f5 7f 12 00 00 00 00 00  c4 bd 11 00 c4 bd 11 00  |................|
00000040  cd 01 00 00 0a 00 00 00  ff 7f 12 00 00 00 00 00  |................|
00000050  a5 3c 10 00 a5 3c 10 00  ce 01 00 00 0a 00 00 00  |.<...<..........|
00000060  09 80 12 00 00 00 00 00  b4 3c 10 00 b4 3c 10 00  |.........<...<..|
00000070  cf 01 00 00 0a 00 00 00  13 80 12 00 00 00 00 00  |................|
00000080  bf 3c 10 00 bf 3c 10 00  d0 01 00 00 0a 00 00 00  |.<...<..........|
00000090  1d 80 12 00 00 00 00 00  c5 3c 10 00 c5 3c 10 00  |.........<...<..|
000000a0  d1 01 00 00 0a 00 00 00  27 80 12 00 00 00 00 00  |........'.......|
000000b0  cf 3c 10 00 cf 3c 10 00  d2 01 00 00 0a 00 00 00  |.<...<..........|
000000c0  31 80 12 00 00 00 00 00  d4 3c 10 00 d4 3c 10 00  |1........<...<..|
000000d0  d3 01 00 00 0a 00 00 00  3b 80 12 00 00 00 00 00  |........;.......|
000000e0  dc 3c 10 00 dc 3c 10 00  d4 01 00 00 0a 00 00 00  |.<...<..........|
000000f0  45 80 12 00 00 00 00 00  ef 3c 10 00 ef 3c 10 00  |E........<...<..|
00000100  d5 01 00 00 0a 00 00 00  4f 80 12 00 00 00 00 00  |........O.......|
00000110  fd 3c 10 00 fd 3c 10 00  d6 01 00 00 0a 00 00 00  |.<...<..........|
00000120  59 80 12 00 00 00 00 00  0d 3d 10 00 0d 3d 10 00  |Y........=...=..|
00000130  d7 01 00 00 0a 00 00 00  63 80 12 00 00 00 00 00  |........c.......|
00000140  1c 3d 10 00 1c 3d 10 00  d8 01 00 00 0a 00 00 00  |.=...=..........|
00000150  6d 80 12 00 00 00 00 00  2d 3d 10 00 2d 3d 10 00  |m.......-=..-=..|
00000160  d9 01 00 00 0a 00 00 00  77 80 12 00 00 00 00 00  |........w.......|
00000170  41 3d 10 00 41 3d 10 00  da 01 00 00 0a 00 00 00  |A=..A=..........|
00000180  81 80 12 00 00 00 00 00  4b 3d 10 00 4b 3d 10 00  |........K=..K=..|
00000190  db 01 00 00 0a 00 00 00  8b 80 12 00 00 00 00 00  |................|
000001a0  58 3d 10 00 58 3d 10 00  dc 01 00 00 0a 00 00 00  |X=..X=..........|
000001b0  95 80 12 00 00 00 00 00  69 3d 10 00 69 3d 10 00  |........i=..i=..|
000001c0  dd 01 00 00 0a 00 00 00  9f 80 12 00 00 00 00 00  |................|
000001d0  78 3d 10 00 78 3d 10 00  de 01 00 00 0a 00 00 00  |x=..x=..........|
000001e0  a9 80 12 00 00 00 00 00  80 3d 10 00 80 3d 10 00  |.........=...=..|
000001f0  df 01 00 00 0a 00 00 00  b3 80 12 00 00 00 00 00  |................|
00000200

---

### Post by presence1960 on 2009-08-21
look at the very bottom of your output:

```
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda5

00000000 e1 7f 12 00 00 00 00 00 82 3c 10 00 82 3c 10 00 |.........<...<..|
00000010 cb 01 00 00 0a 00 00 00 eb 7f 12 00 00 00 00 00 |................|
00000020 40 9f 11 00 97 3c 10 00 cc 01 00 00 0a 00 00 00 |@....<..........|
00000030 f5 7f 12 00 00 00 00 00 c4 bd 11 00 c4 bd 11 00 |................|
00000040 cd 01 00 00 0a 00 00 00 ff 7f 12 00 00 00 00 00 |................|
00000050 a5 3c 10 00 a5 3c 10 00 ce 01 00 00 0a 00 00 00 |.<...<..........|
00000060 09 80 12 00 00 00 00 00 b4 3c 10 00 b4 3c 10 00 |.........<...<..|
00000070 cf 01 00 00 0a 00 00 00 13 80 12 00 00 00 00 00 |................|
00000080 bf 3c 10 00 bf 3c 10 00 d0 01 00 00 0a 00 00 00 |.<...<..........|
00000090 1d 80 12 00 00 00 00 00 c5 3c 10 00 c5 3c 10 00 |.........<...<..|
000000a0 d1 01 00 00 0a 00 00 00 27 80 12 00 00 00 00 00 |........'.......|
000000b0 cf 3c 10 00 cf 3c 10 00 d2 01 00 00 0a 00 00 00 |.<...<..........|
000000c0 31 80 12 00 00 00 00 00 d4 3c 10 00 d4 3c 10 00 |1........<...<..|
000000d0 d3 01 00 00 0a 00 00 00 3b 80 12 00 00 00 00 00 |........;.......|
000000e0 dc 3c 10 00 dc 3c 10 00 d4 01 00 00 0a 00 00 00 |.<...<..........|
000000f0 45 80 12 00 00 00 00 00 ef 3c 10 00 ef 3c 10 00 |E........<...<..|
00000100 d5 01 00 00 0a 00 00 00 4f 80 12 00 00 00 00 00 |........O.......|
00000110 fd 3c 10 00 fd 3c 10 00 d6 01 00 00 0a 00 00 00 |.<...<..........|
00000120 59 80 12 00 00 00 00 00 0d 3d 10 00 0d 3d 10 00 |Y........=...=..|
00000130 d7 01 00 00 0a 00 00 00 63 80 12 00 00 00 00 00 |........c.......|
00000140 1c 3d 10 00 1c 3d 10 00 d8 01 00 00 0a 00 00 00 |.=...=..........|
00000150 6d 80 12 00 00 00 00 00 2d 3d 10 00 2d 3d 10 00 |m.......-=..-=..|
00000160 d9 01 00 00 0a 00 00 00 77 80 12 00 00 00 00 00 |........w.......|
00000170 41 3d 10 00 41 3d 10 00 da 01 00 00 0a 00 00 00 |A=..A=..........|
00000180 81 80 12 00 00 00 00 00 4b 3d 10 00 4b 3d 10 00 |........K=..K=..|
00000190 db 01 00 00 0a 00 00 00 8b 80 12 00 00 00 00 00 |................|
000001a0 58 3d 10 00 58 3d 10 00 dc 01 00 00 0a 00 00 00 |X=..X=..........|
000001b0 95 80 12 00 00 00 00 00 69 3d 10 00 69 3d 10 00 |........i=..i=..|
000001c0 dd 01 00 00 0a 00 00 00 9f 80 12 00 00 00 00 00 |................|
000001d0 78 3d 10 00 78 3d 10 00 de 01 00 00 0a 00 00 00 |x=..x=..........|
000001e0 a9 80 12 00 00 00 00 00 80 3d 10 00 80 3d 10 00 |.........=...=..|
000001f0 df 01 00 00 0a 00 00 00 b3 80 12 00 00 00 00 00 |................|
00000200
```

This is why Ubuntu will not boot. Try this :

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,3)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,3)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

See if that fixes it.

---

### Post by presence1960 on 2009-08-21
holy you know what!! sda5 is your swap! That's why it can't be mounted at boot, you have a bootloader on swap! / and swap and /home mount on boot. I forget how to delete swap partition and make a new one active. maybe someone else can help you  with that. I will search the forums for an answer to that for you.

---

### Post by lincoln32 on 2009-08-21
this is what I got after sudo grub so I assume that it cannot locate grub file?


[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>

---

### Post by presence1960 on 2009-08-21
> **lincoln32 said:**
> this is what I got after sudo grub so I assume that it cannot locate grub file?


[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>

sudo grub
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>find /boot/grub/stage1... etc refer to the guide I posted.

But that is not the problem if you see my previous post # 5. Your sda5 swap partition has an unknown bootloader on it. See the very bottom of your boot info script output. This is preventing you from booting. When you boot ubuntu your / (root), /home  and swap are mounted. your swap has some kind of bootloader on it and thus the GRUB error because it can not be mounted. You can delete the swap partition and create a new one from gparted on the Live CD. Then from the Live CD run this from terminal ```
blkid -c /dev/null
```
Note the UUID of swap sda5 and still from the live cd edit your /etc/fstab file by substituting the UUID of the new swap partition for the old one in fstab. Be careful not to change anything else!. Then reboot and see if it works.

P.S. you can edit etc/fstab by running in terminal > gksu nautilus and on the left mounting your Ubuntu root drive (which won't be Filesytem on the Live Cd as that is the Live CD's Filesystem. navigated to /etc/fstab and open the file and edit only the swap UUID. click save & close the file. You may have to mount Ubuntu partition through places > computer first before running gksu nautilus.

---

### Post by presence1960 on 2009-08-21
Thank God for the Boot Info Script . A case like this shows how valuable it is. How would anyone have known your swap was the problem and that it has an unknown bootloader on it.

---

### Post by lincoln32 on 2009-08-21
ended up reformatting all partions and put all linux partions in a extended partion and it works thanks for the help

---

### Post by presence1960 on 2009-08-21
> **lincoln32 said:**
> ended up reformatting all partions and put all linux partions in a extended partion and it works thanks for the help

Glad you got it working! Any idea how swap got a bootloader on it? That is very strange, actually the first case of that I have seen. Without the boot info script we would probably have never known that. Enjoy Ubuntu.

---

### Post by lincoln32 on 2009-08-21
I have trued several install disks (some I have used before with success)
and all booted weird and had a windows xp log off screen for a moment during boot and several attempts to auto set partions returned root and swap sixes of two hundred mb for both. I also used a boot gparted disk to manually set partions then ubuntu to set mount points. d600 seems to work ok with xp or ubuntu only but not both. Bios? it also has the dock feature that will allow it to boot and run off a remote second harddrive that might cause a conflict locating partions I really am unsure at this point but I also had a grub error 18 at times but since it works I will leave it as is

---

### Post by Hyrum on 2009-10-18
I also have a Dell D600 and I have a Grub error 18 at start up. I ran the boot_info_script and got the text below. Can anyone help me?

> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb08bb08b

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   269,040,554   268,928,100   7 HPFS/NTFS
/dev/sda3         269,040,555   312,576,704    43,536,150   5 Extended
/dev/sda5         269,040,618   310,681,034    41,640,417  83 Linux
/dev/sda6         310,681,098   312,576,704     1,895,607  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-090A" TYPE="vfat" 
/dev/sda2: UUID="9E84E65C84E63705" TYPE="ntfs" 
/dev/sda5: UUID="76b08d64-1f33-46d2-8010-fecf08c3716c" TYPE="ext3" 
/dev/sda6: UUID="755f2571-fd37-4f84-9e37-b6c08d806cb3" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=76b08d64-1f33-46d2-8010-fecf08c3716c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=76b08d64-1f33-46d2-8010-fecf08c3716c

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		76b08d64-1f33-46d2-8010-fecf08c3716c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=76b08d64-1f33-46d2-8010-fecf08c3716c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		76b08d64-1f33-46d2-8010-fecf08c3716c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=76b08d64-1f33-46d2-8010-fecf08c3716c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		76b08d64-1f33-46d2-8010-fecf08c3716c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=76b08d64-1f33-46d2-8010-fecf08c3716c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=755f2571-fd37-4f84-9e37-b6c08d806cb3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 140.5GB: boot/grub/menu.lst
 140.4GB: boot/grub/stage2
 140.4GB: boot/initrd.img-2.6.28-11-generic
 140.4GB: boot/vmlinuz-2.6.28-11-generic
 140.4GB: initrd.img
 140.4GB: vmlinuz

---

### Post by presence1960 on 2009-10-18
GRUB error 18 means you are trying to boot an OS outside of the cylinder boundary that your BIOS can read. See [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors").

Now see the locatiion of GRUB files and Ubuntu boot files:

```
=================== sda5: Location of files loaded by Grub: ===================


140.5GB: boot/grub/menu.lst
140.4GB: boot/grub/stage2
140.4GB: boot/initrd.img-2.6.28-11-generic
140.4GB: boot/vmlinuz-2.6.28-11-generic
140.4GB: initrd.img
140.4GB: vmlinuz 

```

You have 2 options if you want Ubuntu to run:
1. See if there is a BIOS update which will allow your BIOS to read the entire hard disk at boot...or

2. When installing Ubuntu you must create a separate boot partition within the readable boundary so your BIOS can read the files needed to boot. Unless you have a very old BIOS version the readable area is usually the first 137 GB of the hard disk.

---

### Post by Hyrum on 2009-10-25
Thanks! That fixed it. There were no Bios updates available so I reinstalled linux and only used the first 137 GB and it works now. Thanks!

---

