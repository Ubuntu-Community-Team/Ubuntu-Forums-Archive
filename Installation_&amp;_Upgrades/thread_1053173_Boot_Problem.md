---
title: "Boot Problem"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by samarsingla on 2009-01-28
Hello Everyone
I had Vista 32 bit and 64 bit running in dual boot mode. I installed Ubuntu Ultimate edition 64 bit in a seperate partition but I don't get the boot prompt for booting into Ubuntu. I have tried installing the normal Ubuntu 8.04 64 bit also but still the same.
Any help is highly appreciated.
Regards
Samar

---

### Post by digitalbenji on 2009-01-28
Did you install Ubuntu before or after installing Vista?  It sounds like Windows Vista (not sure if its 32 or 64) has control of your Master Boot Record.  I would download the Super Grub Boot Disk and use it to restore your bootloader to have the expected entires.  You can find the Super Grub Boot Disk here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Basically, follow the onscreen menus to install Grub, it should automatically figure out what the needed entries are for each OS you want.  Don't commit any changes or write to the MBR unless you're sure though, because that could leave you without a properly configured bootloader.

---

### Post by samarsingla on 2009-01-28
I tried booting from it and tried to fix GRUB but it said it did not succeed.

---

### Post by caljohnsmith on 2009-01-28
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by samarsingla on 2009-01-28
Here it is..


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /bootmgr /grldr

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 40.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sde2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 63.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3b6f3b6

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *         2,048  204,802,047  204,800,000   7 HPFS/NTFS
/dev/sda2        409,602,048  976,769,023  567,166,976   7 HPFS/NTFS
/dev/sda3        204,812,685  409,593,239  204,780,555   5 Extended
/dev/sda5        204,812,748  401,191,244  196,378,497  83 Linux
/dev/sda6        401,191,308  409,593,239    8,401,932  82 Linux swap / Solaris

/dev/sda2 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073c23

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *        16,065  976,768,064  976,752,000   f W95 Ext'd (LBA)
/dev/sdb5             16,128  976,768,064  976,751,937   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9cec68ac

Partition  Boot        Start          End         Size  Id System

/dev/sdc1    *         2,0481,465,145,3431,465,143,296   7 HPFS/NTFS

/dev/sdc1 ends after the last cylinder of /dev/sdc

Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1be6bd76

Partition  Boot        Start          End         Size  Id System

/dev/sdd1                 63  312,581,807  312,581,745   b W95 FAT32

/dev/sdd1 ends after the last cylinder of /dev/sdd

Drive sde: _____________________________________________________________________

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x625d625d

Partition          Start          End         Size System
/dev/sde1             40      409,639      409,600 System/Boot Partition
/dev/sde2        409,640  101,072,935  100,663,296 -
/dev/sde3    101,335,080  156,301,447   54,966,368 usually Linux

/dev/sde3 ends after the last cylinder of /dev/sde

Drive sdf: _____________________________________________________________________

Disk /dev/sdf: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot        Start          End         Size  Id System

/dev/sdf1                 63    7,864,289    7,864,227   b W95 FAT32

/dev/sdf1 ends after the last cylinder of /dev/sdf

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B60CA4BE0CA47ACF" TYPE="ntfs" 
/dev/sda2: UUID="4C4AB7A44AB7896A" LABEL="work copy" TYPE="ntfs" 
/dev/sda5: UUID="c1e3980b-dc0e-40d9-be10-0e581af4fd6d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="bd3d8a73-da47-42ae-9cf5-4ee24ba533ae" TYPE="swap" 
/dev/sdb5: UUID="BE605D46605D0695" LABEL="work" TYPE="ntfs" 
/dev/sdc1: UUID="5A9495A694958563" LABEL="downloads" TYPE="ntfs" 
/dev/sdd1: LABEL="UNTITLED" UUID="E750-1301" TYPE="vfat" 
/dev/sde1: LABEL="EFI" UUID="4646-150A" TYPE="vfat" 
/dev/sde2: UUID="106A3EEB06C6604C" TYPE="hfsplus" 
/dev/loop0: TYPE="squashfs" 
/dev/sdf1: LABEL="EOS" UUID="3C45-0902" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/UNTITLED type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdf1 on /media/EOS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

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
# kopt=root=UUID=c1e3980b-dc0e-40d9-be10-0e581af4fd6d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c1e3980b-dc0e-40d9-be10-0e581af4fd6d

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
uuid		c1e3980b-dc0e-40d9-be10-0e581af4fd6d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c1e3980b-dc0e-40d9-be10-0e581af4fd6d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c1e3980b-dc0e-40d9-be10-0e581af4fd6d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c1e3980b-dc0e-40d9-be10-0e581af4fd6d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c1e3980b-dc0e-40d9-be10-0e581af4fd6d
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


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c1e3980b-dc0e-40d9-be10-0e581af4fd6d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=bd3d8a73-da47-42ae-9cf5-4ee24ba533ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


 153.6GB: boot/grub/menu.lst
 153.6GB: boot/grub/stage2
 153.6GB: boot/initrd.img-2.6.27-7-generic
 153.7GB: boot/vmlinuz-2.6.27-7-generic
 153.6GB: initrd.img
 153.7GB: vmlinuz

=========================== Unknown MBRs or Boot Sectors =======================

Unknow GPT Partiton Type
005346480000aa11aa1100306543ecac
Unknown BootLoader  on sdd1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 40 20 00  |.X.BSD  4.4..@ .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  71 9e a1 12 04 95 00 00  00 00 00 00 02 00 00 00  |q...............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 01 13 50 e7 55  4e 54 49 54 4c 45 44 20  |..)..P.UNTITLED |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 0a 15 46 46 45  46 49 20 20 20 20 20 20  |..)..FFEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde3

00000000  11 f4 38 e5 df 45 b4 8d  2a ff 56 bc ef 3f 06 e8  |..8..E..*.V..?..|
00000010  8d 5a 35 4b d5 cb 38 ed  d8 7a 14 01 72 96 a8 80  |.Z5K..8..z..r...|
00000020  e0 7b ef 2b 8b 5c 9e 9a  1a 1d 6e ae 39 4b bb 39  |.{.+.\....n.9K.9|
00000030  f6 d3 38 3a 34 61 5e 1c  1b e2 18 06 72 2c cc cd  |..8:4a^.....r,..|
00000040  e8 38 d6 61 bd b7 6b 75  55 c6 90 5d 07 15 36 8b  |.8.a..kuU..]..6.|
00000050  6a fc 08 f0 be ce c7 a0  d8 cd 95 a3 e4 95 bf 63  |j..............c|
00000060  ce 14 59 cd 86 98 d1 9b  f3 89 4e d1 e0 31 80 a0  |..Y.......N..1..|
00000070  81 bc 71 7a 0e c9 b7 6f  5a fa a8 be 5e d3 3b a4  |..qz...oZ...^.;.|
00000080  00 aa a2 ba d6 b6 5f c2  64 40 d8 d8 46 f1 06 07  |......_.d@..F...|
00000090  ab 19 a0 a2 d3 b4 6c fa  f1 ec 9b a4 ad a2 c0 03  |......l.........|
000000a0  3f de f7 51 f1 e5 14 be  4e dc 61 37 2e d3 af 8d  |?..Q....N.a7....|
000000b0  bb 9b d2 5c 1a 70 e2 b5  e3 60 38 a3 60 45 ad 8a  |...\.p...`8.`E..|
000000c0  50 06 5f f7 7f b9 f8 2a  d4 22 89 cf e3 4f bb 0b  |P._....*."...O..|
000000d0  b7 49 a1 44 77 66 cc 91  4e 3b 46 8d fd 26 ed 1a  |.I.Dwf..N;F..&..|
000000e0  a3 b1 23 7b e1 ce 48 cf  8f b5 a5 35 c9 28 e8 03  |..#{..H....5.(..|
000000f0  f3 51 00 d8 7a 0c d8 f8  23 b3 30 02 08 c1 da c8  |.Q..z...#.0.....|
00000100  c0 fc a9 99 13 7c fb 15  12 d1 fb 00 ff 36 22 38  |.....|.......6"8|
00000110  53 2d 97 d6 32 50 5b f9  0e c3 47 c2 a5 8d b9 62  |S-..2P[...G....b|
00000120  a8 59 99 c9 01 54 5b 1a  86 42 0a cf 64 0b 06 8d  |.Y...T[..B..d...|
00000130  3a 90 4f 45 fa 2e c6 d2  3b 72 5a 21 bf 9e 4c e0  |:.OE....;rZ!..L.|
00000140  9f 1c 18 be ac 5e 7c fe  b9 64 3f 16 6d 5a 4c 2b  |.....^|..d?.mZL+|
00000150  79 49 cb 35 18 d3 41 1a  1b 94 25 22 4a ef 42 6a  |yI.5..A...%"J.Bj|
00000160  5b f7 30 98 3b e8 57 4a  41 a3 92 38 7a 77 ac 29  |[.0.;.WJA..8zw.)|
00000170  bc 0e 0a 2b d3 86 3d 51  9b 53 e8 d6 83 a4 fb ae  |...+..=Q.S......|
00000180  e9 47 cb 73 ab bc 0f df  aa f5 dd 0f 91 b6 7c 0b  |.G.s..........|.|
00000190  d9 19 64 11 53 1e a0 a9  86 ac e8 75 15 96 99 bf  |..d.S......u....|
000001a0  e6 a3 c9 52 4f 7f 3c 33  34 50 ff 09 03 20 d2 5a  |...RO.<34P... .Z|
000001b0  13 56 9f a7 0c c1 81 35  a9 d1 eb 09 6d a3 f1 fb  |.V.....5....m...|
000001c0  bd ec 1d 21 e5 24 d6 89  b0 2e fb 94 b9 81 92 b5  |...!.$..........|
000001d0  94 88 52 7c 1c da a5 5b  78 84 92 bd 26 60 31 39  |..R|...[x...&`19|
000001e0  0a 87 fc a8 2c e2 c1 9c  ce 6f f5 9b 4c 7a 10 09  |....,....o..Lz..|
000001f0  40 a9 9f a6 6f d2 b1 7b  f2 d8 64 e4 c4 05 4f 9f  |@...o..{..d...O.|
00000200

Unknown BootLoader  on sdf1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 08 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  a3 ff 77 00 f1 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 02 09 45 3c 45  4f 53 20 20 20 20 20 20  |..)..E<EOS      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sde3: unknown volume type

---

### Post by caljohnsmith on 2009-01-28
It looks like you have Grub installed correctly to the MBR (Master Boot Record) of your sda drive, so if you aren't getting the Grub menu or at least a Grub error on start up, you probably just need to change your BIOS boot order to boot the sda drive before the other drives. Let me know how that goes.

---

### Post by samarsingla on 2009-01-28
Thanks everyone for your support. I tried booting from different hard disks and it solved the problem. Thanks.

---

