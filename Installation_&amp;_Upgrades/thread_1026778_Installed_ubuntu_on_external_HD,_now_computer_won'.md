---
title: "Installed ubuntu on external HD, now computer won't boot"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by SirAlphonso on 2008-12-31
Hi there,

I tried installing ubuntu on a usb external harddrive, and now when I boot my computer I get the error:
> GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 21
This happens regardless of whether or not the external HD I installed ubuntu on is connected to the computer, except when my external HD is attached it gives Error 18 instead of 21.
I wanted to install ubuntu on the external HD in order to keep Windows XP intact on my internal HD so I wouldn't have to worry about losing what was on my Windows XP HD.
At this point I don't even really care about getting ubuntu running, I just want to boot back into Windows. Is there any way?
My computer is an eMachine 2.8 Ghz Intel Celeron with 256 MB of DDR SDRAM.
Any help would be greatly appreciated.

Thanks again.

---

### Post by unutbu on 2008-12-31
First, restore the Windows bootloader to your internal (primary hard drive). Here are instructions on how to do that: [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

If, after you get Windows booting again you would like to try Ubuntu, we can give you instructions on how to install the GRUB bootloader on your external hard drive and without touching your Windows drive.

If you have any problems/questions, post back here and we'll try to help.

---

### Post by SirAlphonso on 2009-01-01
A great many thanks unutbu. It was a bit of an ordeal, because my administrator password was messed up, but I did Windows working again.

I would indeed like to know how to get my external HD ubuntu working, so those instructions would be much appreciated.

Thanks again!

---

### Post by unutbu on 2009-01-01
Okay, to make sure I give you the right commands for your situation, first boot from the LiveCD. Select the option to try Ubuntu (without installing).
Open a terminal (by clicking Applications>Accessories>Terminal).

Please post the output of 
```

sudo fdisk -l
```
(Note "-l" above is a minus lowercase L, not a minus one.)

---

### Post by SirAlphonso on 2009-01-02
I wasn't sure if I should post the fdisk report when my external HD was plugged in, so I did two, one with one without.

Without:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd979f11c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         419        9728    74782575    7  HPFS/NTFS
/dev/sda2               1         418     3357553+   b  W95 FAT32

Partition table entries are not in disk order
ubuntu@ubuntu:~$
```

With:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd979f11c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         419        9728    74782575    7  HPFS/NTFS
/dev/sda2               1         418     3357553+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x505e505d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4780    38395318+  83  Linux
/dev/sdb2            4781        4866      690795    5  Extended
/dev/sdb5            4781        4866      690763+  82  Linux swap / Solaris
ubuntu@ubuntu:~$
```

Thanks again!

---

### Post by unutbu on 2009-01-02
The following will install the GRUB bootloader to your second hard drive.

Boot from the LiveCD. Open a terminal and type:
```

sudo grub
grub> root (hd1,0)   # Tells GRUB to look in /dev/sdb1 for /boot/grub/menu.lst
grub> setup (hd1)    # Writes the GRUB bootloader to /dev/sdb
grub> quit

```

Now when you reboot, go to the BIOS menu. Change the boot order to boot from the external USB drive. Continue the boot process and you should be presented with the GRUB menu, which should allow you to select between Ubuntu and Windows.

If at some point you disconnect the external drive from the machine, the BIOS will try to boot from the external drive, and when it can not find it, it should revert to booting from your internal drive. Since your Windows MBR is untouched, it will take over the boot process and boot Windows.

---

### Post by SirAlphonso on 2009-01-02
Thanks utunbu.

I tried the commands, but when I got to the second step and entered root (hdl,0), it gave me this error:
```
Error 23: Error while parsing number
```
Edit: wait I think I mistook the 1 for an l.
Edit: I got it working.

---

### Post by unutbu on 2009-01-02
Here, use one's, not L's :)

---

### Post by SirAlphonso on 2009-01-02
Spoke too soon I did.
I ran the commands listed above, shuffled the boot priorities in my BIOS, and when I restart it gives me an error.
It says something about client mac address, then:
```
DHCP....
PXE-E53 No boot device received
PXE-MOF Exiting Intel boot agent
```
Then it boots straight into Windows.

---

### Post by unutbu on 2009-01-02
The Intel boot agent is a different bootloader than GRUB. It appears the BIOS is not properly handing off to the GRUB bootloader. The following command will tell us more about your boot setup.

Please boot from the LiveCD once more, open a terminal and
type (or copy-and-paste):

```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

The output will be a file called RESULTS.txt. Please post the contents of that file here.

---

### Post by SirAlphonso on 2009-01-02
Here are the results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       149565149 sectors, but according to the info from 
                       fdisk, it has 149565150 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd979f11c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     6715170   156280319    74782575    7  HPFS/NTFS
/dev/sda2              63     6715169     3357553+   b  W95 FAT32

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x505e505d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    76790699    38395318+  83  Linux
/dev/sdb2        76790700    78172289      690795    5  Extended
/dev/sdb5        76790763    78172289      690763+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="2818A12F18A0FD46" TYPE="ntfs" 
/dev/sda2: UUID="423B-2BDF" TYPE="vfat" 
/dev/sdb1: UUID="9b46c82e-20ff-471f-8bd3-594ad77206dd" TYPE="ext3" 
/dev/sdb5: UUID="f0ca058a-7e51-44cf-926f-9cc4ad44f1f3" TYPE="swap" 
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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
Unknown BootLoader  on /dev/sda2

00000000  e9 a9 00 52 45 43 4f 56  45 52 59 00 02 08 26 00  |...RECOVERY...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  e0 76 66 00 91 19 00 00  00 00 00 00 02 00 00 00  |.vf.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 df 2b 3b 42 20  20 20 20 20 20 20 20 20  |..).+;B         |
00000050  20 20 46 41 54 33 32 20  20 20 66 c1 e0 02 8b d0  |  FAT32   f.....|
00000060  81 e2 ff 01 66 c1 e8 09  66 3b 46 f8 74 2a 66 89  |....f...f;F.t*f.|
00000070  46 f8 66 03 46 f4 66 0f  b6 5e 28 80 e3 0f 74 0f  |F.f.F.f..^(...t.|
00000080  3a 5e 10 0f 83 8d 00 66  0f af 5e 24 66 03 c3 bb  |:^.....f..^$f...|
00000090  e0 07 b9 01 00 e8 d2 00  8b da 66 8b 87 00 7e 66  |..........f...~f|
000000a0  25 ff ff ff 0f 66 3d f8  ff ff 0f c3 33 c9 8e d9  |%....f=.....3...|
000000b0  8e c1 8e d1 bc f4 7b bd  00 7c 66 0f b6 46 10 66  |......{..|f..F.f|
000000c0  f7 66 24 66 0f b7 56 0e  66 03 56 1c 66 89 56 f4  |.f$f..V.f.V.f.V.|
000000d0  66 03 c2 66 89 46 fc 66  c7 46 f8 ff ff ff ff 66  |f..f.F.f.F.....f|
000000e0  8b 46 2c 66 50 e8 a4 00  bb 70 00 b9 01 00 e8 79  |.F,fP....p.....y|
000000f0  00 bf 00 07 b1 0b be 9d  7d f3 a6 74 2a 03 f9 83  |........}..t*...|
00000100  c7 15 81 ff 00 09 72 ec  66 40 4a 75 db 66 58 e8  |......r.f@Ju.fX.|
00000110  48 ff 72 cf be a8 7d ac  84 c0 74 09 b4 0e bb 07  |H.r...}...t.....|
00000120  00 cd 10 eb f2 cd 18 66  58 ff 75 09 ff 75 0f 66  |.......fX.u..u.f|
00000130  58 66 83 f8 02 72 dd 66  3d f8 ff ff 0f 73 d5 66  |Xf...r.f=....s.f|
00000140  50 e8 48 00 3e 8b 9e 68  01 32 ed 8a 4e 0d e8 19  |P.H.>..h.2..N...|
00000150  00 c1 e1 05 3e 01 8e 68  01 66 58 e8 fc fe 72 d1  |....>..h.fX...r.|
00000160  8a 56 40 ea 00 00 00 20  00 20 66 60 66 6a 00 66  |.V@.... . f`fj.f|
00000170  50 53 6a 00 51 6a 10 8b  f4 b8 00 42 8a 56 40 cd  |PSj.Qj.....B.V@.|
00000180  13 83 c4 10 be c0 7d 72  8e 66 61 c3 66 48 66 48  |......}r.fa.fHfH|
00000190  66 0f b6 56 0d 66 f7 e2  66 03 46 fc c3 4e 54 4c  |f..V.f..f.F..NTL|
000001a0  44 52 20 20 20 20 20 20  0d 0a 49 6e 76 61 6c 69  |DR      ..Invali|
000001b0  64 20 53 79 73 74 65 6d  20 44 69 73 6b 20 6f 72  |d System Disk or|
000001c0  0d 0a 44 69 73 6b 20 49  2f 4f 20 65 72 72 6f 72  |..Disk I/O error|
000001d0  0d 0a 50 72 65 73 73 20  61 20 6b 65 79 20 74 6f  |..Press a key to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


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
# kopt=root=UUID=9b46c82e-20ff-471f-8bd3-594ad77206dd ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=9b46c82e-20ff-471f-8bd3-594ad77206dd

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
uuid		9b46c82e-20ff-471f-8bd3-594ad77206dd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b46c82e-20ff-471f-8bd3-594ad77206dd ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9b46c82e-20ff-471f-8bd3-594ad77206dd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b46c82e-20ff-471f-8bd3-594ad77206dd ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9b46c82e-20ff-471f-8bd3-594ad77206dd
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9b46c82e-20ff-471f-8bd3-594ad77206dd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=f0ca058a-7e51-44cf-926f-9cc4ad44f1f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 11936
drwxr-xr-x  3 root root    4096 2008-12-31 18:57 .
drwxr-xr-x 20 root root    4096 2008-12-31 18:57 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-31 18:57 grub
-rw-r--r--  1 root root 8163942 2008-12-31 18:57 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-31 18:57 .
drwxr-xr-x 3 root root   4096 2008-12-31 18:57 ..
-rw-r--r-- 1 root root    197 2008-12-31 18:57 default
-rw-r--r-- 1 root root     30 2008-12-31 18:57 device.map
-rw-r--r-- 1 root root   8108 2008-12-31 18:57 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-31 18:57 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-31 18:57 installed-version
-rw-r--r-- 1 root root   8712 2008-12-31 18:57 jfs_stage1_5
-rw-r--r-- 1 root root   4825 2008-12-31 18:57 menu.lst
-rw-r--r-- 1 root root   4321 2008-12-31 18:57 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-31 18:57 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-31 18:57 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-31 18:57 stage1
-rw-r--r-- 1 root root 121460 2008-12-31 18:57 stage2
-rw-r--r-- 1 root root   9556 2008-12-31 18:57 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by unutbu on 2009-01-02
Everything looks perfectly setup as far as Linux is concerned. 
Are you sure you have the right BIOS settings to boot the external HD first?

Sorry I can't be more help. I'm rather stumped by this.

---

### Post by SirAlphonso on 2009-01-02
It looks like there is just something wonky going on with my computer.
I pressed F10 at boot to specifically select my boot device and it gave me the Grub error I got earlier. So I got my roommates computer, plugged my external HD into it and ubuntu loaded fine.

---

### Post by meierfra. on 2009-01-05
Some bios refuse to boot a hard drive without a boot flag.
Try this:

```
sudo sfdisk -A1 /dev/sdb
```

---

