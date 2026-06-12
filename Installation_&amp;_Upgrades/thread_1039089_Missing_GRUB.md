---
title: "Missing GRUB"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by OneRingShort on 2009-01-14
I ran into a problem I've never encounter before while installing Ubuntu back onto my computer after a motherboard upgrade.  I installed Vista first so that GRUB will overwrite it.  I then installed Ubuntu 8.10 on the same hard drive.  When it asked to restart, I complied, but found that I was not presented with a boot loader, and instead, it just booted back into Windows.  I tried restoring GRUB (ala [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")), but the problem persists.  Any suggestions on what to try next?

Hardware:
nVidia 750i
4g DDR2 1066 RAM
4 hard drives (2 in RAID 1 through a PCI-e raid controller)

---

### Post by caljohnsmith on 2009-01-14
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by OneRingShort on 2009-01-14
Sorry for the delay.  Here's what it spat out:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc1 sdc1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc1 sdc1 ntfs-3g force 0 0

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc6: _________________________________________________________________________

    File system:       swap

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d64f1d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   625012735   312505344    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d64f1d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   625012735   312505344    7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: partition 1 does not end at a cylinder boundary

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc398d2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   501762047   250880000    7  HPFS/NTFS
/dev/sdc2       501774210   898258409   198242100    5  Extended
/dev/sdc5       501774273   892394684   195310206   83  Linux
/dev/sdc6       892394748   898258409     2931831   82  Linux swap / Solaris

sfdisk -V /dev/sdc:

Warning: partition 1 does not end at a cylinder boundary

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf004bac3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001   83  Linux

sfdisk -V /dev/sdd:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdd: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="A6D45EB9D45E8B85" LABEL="Vista Longhorn" TYPE="ntfs" 
/dev/sdc5: UUID="3a931b06-1bee-4ca1-8bd5-3989ece74b81" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc6: UUID="9558d1cb-9638-4465-9f38-c0d0bd03f4af" TYPE="swap" 
/dev/sdd1: UUID="cab64685-04a4-4750-aef0-bae0d68fdbe4" SEC_TYPE="ext2" TYPE="ext3" 
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
/dev/scd1 on /media/BF2142 DVD type udf (ro,nosuid,nodev,uhelper=hal,uid=999)
/dev/scd2 on /media/UT3_RC7 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)

=========================== sdc5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3a931b06-1bee-4ca1-8bd5-3989ece74b81 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a931b06-1bee-4ca1-8bd5-3989ece74b81

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
uuid		3a931b06-1bee-4ca1-8bd5-3989ece74b81
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3a931b06-1bee-4ca1-8bd5-3989ece74b81 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3a931b06-1bee-4ca1-8bd5-3989ece74b81
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3a931b06-1bee-4ca1-8bd5-3989ece74b81 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3a931b06-1bee-4ca1-8bd5-3989ece74b81
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
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=3a931b06-1bee-4ca1-8bd5-3989ece74b81 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd1
UUID=cab64685-04a4-4750-aef0-bae0d68fdbe4 /home           ext3    relatime        0       2
# /dev/sdc6
UUID=9558d1cb-9638-4465-9f38-c0d0bd03f4af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc5/boot: ==================================

total 11952
drwxr-xr-x  3 root root    4096 2009-01-14 11:15 .
drwxr-xr-x 20 root root    4096 2009-01-14 11:14 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-14 11:15 grub
-rw-r--r--  1 root root 8180159 2009-01-14 11:14 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdc5/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-14 11:15 .
drwxr-xr-x 3 root root   4096 2009-01-14 11:15 ..
-rw-r--r-- 1 root root    197 2009-01-14 11:15 default
-rw-r--r-- 1 root root     60 2009-01-14 11:15 device.map
-rw-r--r-- 1 root root   8108 2009-01-14 11:15 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-14 11:15 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-14 11:15 installed-version
-rw-r--r-- 1 root root   8712 2009-01-14 11:15 jfs_stage1_5
-rw-r--r-- 1 root root   4653 2009-01-14 11:15 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-14 11:15 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-14 11:15 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-14 11:15 stage1
-rw-r--r-- 1 root root 121460 2009-01-14 11:15 stage2
-rw-r--r-- 1 root root   9556 2009-01-14 11:15 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda1

00000000  71 2a 6a ed 62 d7 5d a9  10 49 e7 8f 4d 43 1d 17  |q*j.b.]..I..MC..|
00000010  80 7f 9b 92 74 b3 df 83  57 95 2a a9 bf 80 67 46  |....t...W.*...gF|
00000020  38 36 42 2a 19 71 05 f6  a1 48 21 be 73 c4 4c 3d  |86B*.q...H!.s.L=|
00000030  67 18 f5 88 0d 74 fe 0d  5b ac 3e 54 34 2f 9d 59  |g....t..[.>T4/.Y|
00000040  a8 4e f4 91 3f f2 80 fa  18 1d e7 69 b0 9d 6a 45  |.N..?......i..jE|
00000050  2f 12 8a 1a 33 07 bd 7d  b3 da 02 50 14 45 cc b6  |/...3..}...P.E..|
00000060  f2 d1 5e 16 d8 8f 59 05  6d 41 dd 74 9e 22 19 e8  |..^...Y.mA.t."..|
00000070  06 11 46 f1 47 02 c5 2c  a9 84 c8 aa b5 c9 80 51  |..F.G..,.......Q|
00000080  9d 41 13 0c e6 22 26 4c  d7 b1 fb 03 63 68 d8 d7  |.A..."&L....ch..|
00000090  6f c9 e2 cd 31 25 d4 37  2f 06 71 2b 8d cc 49 69  |o...1%.7/.q+..Ii|
000000a0  74 c9 ef d6 38 52 86 5a  ab 37 ab da 70 69 95 9f  |t...8R.Z.7..pi..|
000000b0  7a 10 89 11 cf e6 66 f0  d1 28 44 98 32 8a 85 dd  |z.....f..(D.2...|
000000c0  63 9a 28 64 7e 03 67 05  70 2f a9 6f fa 97 6b 1a  |c.(d~.g.p/.o..k.|
000000d0  c1 b6 e1 97 9c 70 43 2b  8b ad 51 46 78 25 19 5e  |.....pC+..QFx%.^|
000000e0  29 d9 37 cd 29 33 1c 67  8c 5d 4c 3b 1f e7 cf a9  |).7.)3.g.]L;....|
000000f0  ca ed 7e 4e dd 73 a0 c7  28 64 47 1a 6b fa ff 7f  |..~N.s..(dG.k...|
00000100  56 c2 14 91 e5 4f a7 05  cd fb 1c 00 e2 a8 72 97  |V....O........r.|
00000110  cf bd 6c fc f7 5d fc f8  ed 23 51 90 8b 84 aa d7  |..l..]...#Q.....|
00000120  d7 fa dd 86 16 1a be 11  38 74 55 01 36 6c 20 3f  |........8tU.6l ?|
00000130  4c c6 ac ea 46 35 29 f0  f3 ef 65 9e 3e d1 c5 90  |L...F5)...e.>...|
00000140  d4 e7 46 a1 6b f9 e1 b2  b5 3b 19 63 e1 03 65 cf  |..F.k....;.c..e.|
00000150  3d 40 9a 6d 94 24 42 fb  31 ce 35 c0 f7 cd 5d d8  |=@.m.$B.1.5...].|
00000160  96 a3 0f 3e ed 08 ee c5  f1 d1 c4 17 de a4 5b de  |...>..........[.|
00000170  28 12 b4 24 25 48 ba ae  1c 90 95 e1 98 ec 16 37  |(..$%H.........7|
00000180  45 a6 8f e2 85 81 28 55  ab 60 0d 4e bd 5f 58 96  |E.....(U.`.N._X.|
00000190  bc 99 ec 7a 67 21 f4 22  3b 55 83 e8 ad 16 72 82  |...zg!.";U....r.|
000001a0  4b bd dd 9b 32 e6 68 7a  c2 84 01 a8 9d 11 9e c5  |K...2.hz........|
000001b0  7c 83 0e f7 5d ce 84 86  ea 3a f5 b9 05 62 7b cd  ||...]....:...b{.|
000001c0  4a 53 80 6a a4 5e 2f 15  26 b9 37 00 fd 7c dc b5  |JS.j.^/.&.7..|..|
000001d0  3f f5 e6 09 c9 05 e1 1a  09 1d e1 88 21 71 a8 36  |?...........!q.6|
000001e0  13 a7 bc 77 fe f2 d8 f0  ae 54 20 a4 e4 1f 09 df  |...w.....T .....|
000001f0  9d 66 f3 c9 10 f6 c0 42  0f 69 8b 45 41 9b 4d b6  |.f.....B.i.EA.M.|
00000200

Unknown BootLoader  on /dev/sdb1

00000000  71 2a 6a ed 62 d7 5d a9  10 49 e7 8f 4d 43 1d 17  |q*j.b.]..I..MC..|
00000010  80 7f 9b 92 74 b3 df 83  57 95 2a a9 bf 80 67 46  |....t...W.*...gF|
00000020  38 36 42 2a 19 71 05 f6  a1 48 21 be 73 c4 4c 3d  |86B*.q...H!.s.L=|
00000030  67 18 f5 88 0d 74 fe 0d  5b ac 3e 54 34 2f 9d 59  |g....t..[.>T4/.Y|
00000040  a8 4e f4 91 3f f2 80 fa  18 1d e7 69 b0 9d 6a 45  |.N..?......i..jE|
00000050  2f 12 8a 1a 33 07 bd 7d  b3 da 02 50 14 45 cc b6  |/...3..}...P.E..|
00000060  f2 d1 5e 16 d8 8f 59 05  6d 41 dd 74 9e 22 19 e8  |..^...Y.mA.t."..|
00000070  06 11 46 f1 47 02 c5 2c  a9 84 c8 aa b5 c9 80 51  |..F.G..,.......Q|
00000080  9d 41 13 0c e6 22 26 4c  d7 b1 fb 03 63 68 d8 d7  |.A..."&L....ch..|
00000090  6f c9 e2 cd 31 25 d4 37  2f 06 71 2b 8d cc 49 69  |o...1%.7/.q+..Ii|
000000a0  74 c9 ef d6 38 52 86 5a  ab 37 ab da 70 69 95 9f  |t...8R.Z.7..pi..|
000000b0  7a 10 89 11 cf e6 66 f0  d1 28 44 98 32 8a 85 dd  |z.....f..(D.2...|
000000c0  63 9a 28 64 7e 03 67 05  70 2f a9 6f fa 97 6b 1a  |c.(d~.g.p/.o..k.|
000000d0  c1 b6 e1 97 9c 70 43 2b  8b ad 51 46 78 25 19 5e  |.....pC+..QFx%.^|
000000e0  29 d9 37 cd 29 33 1c 67  8c 5d 4c 3b 1f e7 cf a9  |).7.)3.g.]L;....|
000000f0  ca ed 7e 4e dd 73 a0 c7  28 64 47 1a 6b fa ff 7f  |..~N.s..(dG.k...|
00000100  56 c2 14 91 e5 4f a7 05  cd fb 1c 00 e2 a8 72 97  |V....O........r.|
00000110  cf bd 6c fc f7 5d fc f8  ed 23 51 90 8b 84 aa d7  |..l..]...#Q.....|
00000120  d7 fa dd 86 16 1a be 11  38 74 55 01 36 6c 20 3f  |........8tU.6l ?|
00000130  4c c6 ac ea 46 35 29 f0  f3 ef 65 9e 3e d1 c5 90  |L...F5)...e.>...|
00000140  d4 e7 46 a1 6b f9 e1 b2  b5 3b 19 63 e1 03 65 cf  |..F.k....;.c..e.|
00000150  3d 40 9a 6d 94 24 42 fb  31 ce 35 c0 f7 cd 5d d8  |=@.m.$B.1.5...].|
00000160  96 a3 0f 3e ed 08 ee c5  f1 d1 c4 17 de a4 5b de  |...>..........[.|
00000170  28 12 b4 24 25 48 ba ae  1c 90 95 e1 98 ec 16 37  |(..$%H.........7|
00000180  45 a6 8f e2 85 81 28 55  ab 60 0d 4e bd 5f 58 96  |E.....(U.`.N._X.|
00000190  bc 99 ec 7a 67 21 f4 22  3b 55 83 e8 ad 16 72 82  |...zg!.";U....r.|
000001a0  4b bd dd 9b 32 e6 68 7a  c2 84 01 a8 9d 11 9e c5  |K...2.hz........|
000001b0  7c 83 0e f7 5d ce 84 86  ea 3a f5 b9 05 62 7b cd  ||...]....:...b{.|
000001c0  4a 53 80 6a a4 5e 2f 15  26 b9 37 00 fd 7c dc b5  |JS.j.^/.&.7..|..|
000001d0  3f f5 e6 09 c9 05 e1 1a  09 1d e1 88 21 71 a8 36  |?...........!q.6|
000001e0  13 a7 bc 77 fe f2 d8 f0  ae 54 20 a4 e4 1f 09 df  |...w.....T .....|
000001f0  9d 66 f3 c9 10 f6 c0 42  0f 69 8b 45 41 9b 4d b6  |.f.....B.i.EA.M.|
00000200


=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
/dev/sdb1: unknown volume type
```

I noticed that the sda1 and sdb1 disks are empty/unknown and would like to point out that those are the two 320g hard drives in RAID 1 on the PCI-e raid controller.

I'm going to have to keep this script, seems rather handy.

---

### Post by caljohnsmith on 2009-01-14
OK, it looks like your RAID array is what has caused the complication. Can you set your BIOS to boot the 500 GB Ubuntu drive? If so, that could be an easy solution to your dilemma. If you can do that, you would just need to install Grub to the MBR (Master Boot Record) of the Ubuntu drive by doing:
```
sudo grub
grub> root (hd2,4)
grub> setup (hd2)
grub> quit
```
Then reboot, set your BIOS to boot the Ubuntu drive, and if all goes well you should be able to boot into Ubuntu. There's a reasonable chance that the Windows entry in your Grub menu might work to boot Windows, but if it doesn't, let me know and we can most likely get Windows booting from the Grub menu too. Let me know how it goes or if you run into problems. :)

---

### Post by OneRingShort on 2009-01-14
I just checked my BIOS, and it doesn't look like its going to be so easy.  Boot order is sdc, sdd, sda/sdb (RAID).

---

### Post by caljohnsmith on 2009-01-14
> **OneRingShort said:**
> I just checked my BIOS, and it doesn't look like its going to be so easy.  Boot order is sdc, sdd, sda/sdb (RAID).
So you're saying that the Ubuntu sdc drive is all ready first in the BIOS boot order? Is sdc1 just a data NTFS partition, or does it also have a Windows install? If sdc1 is just data, then I how about running the Grub commands from my previous post to make the sdc drive bootable, and hopefully that should be all it takes. Let me know how it goes.

---

### Post by OneRingShort on 2009-01-14
Yes, the hard drive contain both Ubuntu and Windows is on the primary boot device, and sdc1 is the Windows installation.  As far as the commands go, those are the ones I tried when GRUB didn't install the first time, and unfortunately didn't provide any results.

I've personally never seen anything like this...I would always at least get an error code I could look up.  Do you think that if this persists that a program like EasyBCD would be able to access the Ubuntu install?  or perhaps is there a larger underlying conflict with the multiple operating systems and the raid controller?

---

### Post by caljohnsmith on 2009-01-14
> **OneRingShort said:**
> Yes, the hard drive contain both Ubuntu and Windows is on the primary boot device, and sdc1 is the Windows installation.  As far as the commands go, those are the ones I tried when GRUB didn't install the first time, and unfortunately didn't provide any results.

I've personally never seen anything like this...I would always at least get an error code I could look up.  Do you think that if this persists that a program like EasyBCD would be able to access the Ubuntu install?  or perhaps is there a larger underlying conflict with the multiple operating systems and the raid controller?
When you previously ran the Grub commands, did you use "setup (hd0)" or "setup (hd2)" like from my previous post? Can you please post the output of the Grub commands from post #4 so I can see the result? Using EasyBCD would probably work, but it may not be necessary if we can find the root cause of why the Ubuntu drive won't boot with some more troubleshooting. It's up to you though.

---

### Post by OneRingShort on 2009-01-14
Oh, nice catch.  I didn't notice that slight difference.  I'll give it a try in a bit (got some things I need to finish first)

---

### Post by OneRingShort on 2009-01-14
> **caljohnsmith said:**
> When you previously ran the Grub commands, did you use "setup (hd0)" or "setup (hd2)" like from my previous post?

That did the trick!  The Ibex is up and running without a problem.

Thanks for the support

Matt

---

### Post by caljohnsmith on 2009-01-14
Glad that did the trick; cheers and enjoy your new Ubuntu install. :)

---

### Post by OneRingShort on 2009-01-16
Ah...it's not quite fixed....turns out Windows won't boot now.  It turns up an Error 13.  I found a thread on it about modifying the menu.lst file, but it's entry is identical to mine (outside of the hard drive number being different b/c of the RAID setup).

Here's mine:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista/Longhorn (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

---

### Post by caljohnsmith on 2009-01-16
You mentioned previously that Windows is on the same drive as Ubuntu, true? If that is the case, how about trying this entry for Windows:
```
title Windows
root (hd0,0)
chainloader +1
```
Let me know if that works.

---

### Post by OneRingShort on 2009-01-16
That did the trick!  Almost got everything sorted out now.  Thanks again.

---

