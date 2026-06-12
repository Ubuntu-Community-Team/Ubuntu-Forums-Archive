---
title: "Dual Booting"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by wide-load on 2009-02-19
I just added a new SATA drive in a machine that has been running Windows XP.  Windows runs on a SATA drive.  Windows labeled it the M: drive.  I have a Multi Card Reader.  That is why the drive it got such a high designation.  The MBR is on an 20 GB IDE drive, that is primarily used by Windows for backup purposes.

I'm having trouble getting Grub to work.  I made the drive with Ubuntu on it the 1st drive in my boot order.  When the system boots I get the normal Grub Boot Menu.  However if I cursor down to Windows XP Professional in the menu Windows doesn't load.

I did run the boot_info script from SourceForge and below is it's output.

I think I just need to get the code in menu.lst right to be able to boot Windows XP.

Any suggestions would be appreciated.

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sde1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x034b034b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   c W95 FAT32 (LBA)


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabacc689

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,311,184   476,311,122   7 HPFS/NTFS
/dev/sdb2         476,311,185   488,392,064    12,080,880   5 Extended
/dev/sdb5         476,311,248   488,392,064    12,080,817  82 Linux swap / Solaris


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002b17e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   476,262,989   476,262,927  83 Linux
/dev/sdc2         476,262,990   488,392,064    12,129,075   5 Extended
/dev/sdc5         476,263,053   488,392,064    12,129,012  82 Linux swap / Solaris


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 1018 MB, 1018691584 bytes
16 heads, 63 sectors/track, 1973 cylinders, total 1989632 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37b637b5

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     1,989,631     1,989,569   e W95 FAT16 (LBA)

/dev/sdd1 ends after the last cylinder of /dev/sdd

Drive sde: _____________________________________________________________________

Disk /dev/sde: 8 MB, 8388608 bytes
2 heads, 32 sectors/track, 256 cylinders, total 16384 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32        16,383        16,352   1 FAT12


Drive sdf: _____________________________________________________________________

Disk /dev/sdf: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x855bf51c

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   241,248,104   241,248,042   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="BACKUPS" UUID="A0B7-C554" TYPE="vfat" 
/dev/sdb1: UUID="8E1CFC541CFC3933" TYPE="ntfs" 
/dev/sdb5: UUID="3fb40156-a502-446d-a2dc-e34de6f8bcf2" TYPE="swap" 
/dev/sdc1: UUID="d24e9409-e601-495e-a55f-8a55c465ad60" TYPE="ext3" 
/dev/sdc5: UUID="3abe089d-4beb-459c-bc12-b80bcf97b7da" TYPE="swap" 
/dev/sdd1: SEC_TYPE="msdos" UUID="3DEE-005A" TYPE="vfat" 
/dev/sde1: SEC_TYPE="msdos" UUID="11E6-0061" TYPE="vfat" 
/dev/sdf1: LABEL="IOMEGA_HDD" UUID="574E-7642" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/greg/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=greg)
/dev/sdf1 on /media/IOMEGA_HDD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sde1 on /media/disk-1 type vfat (ro,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


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
# kopt=root=UUID=d24e9409-e601-495e-a55f-8a55c465ad60 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d24e9409-e601-495e-a55f-8a55c465ad60

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		d24e9409-e601-495e-a55f-8a55c465ad60
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d24e9409-e601-495e-a55f-8a55c465ad60 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d24e9409-e601-495e-a55f-8a55c465ad60
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d24e9409-e601-495e-a55f-8a55c465ad60 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d24e9409-e601-495e-a55f-8a55c465ad60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d24e9409-e601-495e-a55f-8a55c465ad60 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d24e9409-e601-495e-a55f-8a55c465ad60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d24e9409-e601-495e-a55f-8a55c465ad60 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d24e9409-e601-495e-a55f-8a55c465ad60
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd3,0)
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
# /dev/sdb1
UUID=d24e9409-e601-495e-a55f-8a55c465ad60 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=3abe089d-4beb-459c-bc12-b80bcf97b7da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  24.6GB: boot/grub/menu.lst
  24.6GB: boot/grub/stage2
  24.6GB: boot/initrd.img-2.6.27-11-generic
  24.6GB: boot/initrd.img-2.6.27-7-generic
  24.5GB: boot/vmlinuz-2.6.27-11-generic
  24.6GB: boot/vmlinuz-2.6.27-7-generic
  24.6GB: initrd.img
  24.6GB: initrd.img.old
  24.5GB: vmlinuz
  24.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 20 01 00  |.<.DOK01.02.. ..|
00000010  02 00 02 00 00 f8 f3 00  3f 00 10 00 3f 00 00 00  |........?...?...|
00000020  c1 5b 1e 00 80 00 29 5a  00 ee 3d 00 00 00 00 00  |.[....)Z..=.....|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200

Unknown BootLoader  on sde1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 04 01 00  |.<.DOK01.02.....|
00000010  02 00 02 e0 3f f8 0c 00  20 00 02 00 20 00 00 00  |....?... ... ...|
00000020  00 00 00 00 80 00 29 61  00 e6 11 00 00 00 00 00  |......)a........|
00000030  00 00 00 00 00 00 46 41  54 31 32 20 20 20 33 c9  |......FAT12   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdg sdh sdi sdj

---

### Post by caljohnsmith on 2009-02-19
From the script results it looks like you installed Windows to your 250 GB sdb drive, but unfortunately Windows put its boot files in the sda1 partition on your 20 GB sda drive. It would be best to move the boot files back to the sdb1 Windows partition, reconfigure boot.ini, and then we can configure Grub to boot that partition. So how about doing:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sdb1
sudo rm /mnt/sda1/NTLDR /mnt/sda1/BOOT.INI
gksudo gedit /mnt/sdb1/boot.ini
```
And change the "rdisk(1)" number to 0:
```
[boot loader]
timeout=15
default=multi(0)disk(0)[COLOR="Blue"]rdisk(0)[/COLOR]partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)[COLOR="Blue"]rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your existing Windows entry with the following four entries:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title       Windows XP (hd3)
rootnoverify     (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title       Windows XP (hd4)
rootnoverify     (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
Then reboot, try each of the Windows entries, and if all goes well one of them should work. Once you know which works you can of course delete the others from your menu.lst. If none work, let me know exactly what happens when you try each one, and we can work from there.

---

### Post by wide-load on 2009-02-19
OK.  I did do that and the only one that worked was hd2.  When I ckicked on it, it gave me 2 choices.  Windows XP Pro and Windows Default.  If I hit enter on Windows XP Pro it gives an error message.  If I hit enter on Windows Default it loads Window normally.

So I went into menu.lst and commented out all the references except for hd2.  Now it only gives me that option, with the 2 choices.

Here is the part of menu.lst that deals with Windows.

-----------------------------------------------------------------

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
#title       Windows XP (hd1)
#rootnoverify     (hd1,0)
#map        (hd0) (hd1)
#map        (hd1) (hd0)
#chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

#title       Windows XP (hd3)
#rootnoverify     (hd3,0)
#map        (hd0) (hd3)
#map        (hd3) (hd0)
#chainloader +1

#title       Windows XP (hd4)
#rootnoverify     (hd4,0)
#ap        (hd0) (hd4)
#map        (hd4) (hd0)
#chainloader +1

------------------------------------------------
Can I change it so I do not get both choices and go will go direct to the entry labeled Windows Default?

---

### Post by caljohnsmith on 2009-02-19
Did you change the two instances of "rdisk" in the boot.ini file to use 0, or did you only change rdisk? How about posting:
```
sudo mount /dev/sdb1 /mnt/sdb1 && cat /mnt/sdb1/boot.ini
```

---

### Post by wide-load on 2009-02-19
When I did that I got:
greg@Dual-Core6400:~$ sudo mount /dev/sdb1 /mnt/sdb1 && cat /mnt/sdb1/boot.ini
mount: /dev/sdb1 already mounted or /mnt/sdb1 busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt/sdb1

---

### Post by caljohnsmith on 2009-02-19
OK, I didn't realize you still have sdb1 mounted, so you can just do:
```
cat /mnt/sdb1/boot.ini
```

---

### Post by wide-load on 2009-02-19
To that I got:

greg@Dual-Core6400:~$ cat /mnt/sdb1/boot.ini
cat: /mnt/sdb1/boot.ini: No such file or directory

---

### Post by caljohnsmith on 2009-02-19
OK, that might explain it then--it looks like you could be missing the boot.ini file. How about doing:
```
sudo mount /dev/sda1 /mnt/sda1
ls -l /mnt/sda1 /mnt/sdb1

```
And don't worry if the first command tells you sda1 is all ready mounted.

---

### Post by wide-load on 2009-02-19
To that I got:

greg@Dual-Core6400:~$ sudo mount /dev/sda1 /mnt/sda1
greg@Dual-Core6400:~$ ls -l /mnt/sda1 /mnt/sdb1
/mnt/sda1:
total 2095562
-rwxrwxrwx 1 root root        223 2009-02-19 11:55 boot.ini
-rwxrwxrwx 1 root root        223 2008-07-23 16:37 boot.ini~
-rwxrwxrwx 1 root root        223 2009-02-19 11:55 boot.org
drwxrwxrwx 1 root root       4096 2008-06-23 22:38 Documents and Settings
drwxrwxrwx 1 root root          0 2008-07-03 21:02 Garmin
-rwxrwxrwx 2 root root        256 2008-05-15 23:40 __IOM_DEVLIB__.__ATTRIBUTES__
drwxrwxrwx 1 root root          0 2008-05-15 22:55 MyWorks
-rwxrwxrwx 1 root root      47564 2004-08-04 02:38 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-07-16 10:20 ntldr
-rwxrwxrwx 1 root root 2145386496 2009-02-19 12:18 pagefile.sys
drwxrwxrwx 1 root root      24576 2009-02-14 09:27 Program Files
drwxrwxrwx 1 root root          0 2008-05-14 09:18 RECYCLER
drwxrwxrwx 1 root root       8192 2009-01-23 09:25 ScanSoft Documents
drwxrwxrwx 1 root root       4096 2009-01-25 22:02 System Volume Information
drwxrwxrwx 1 root root          0 2008-06-24 00:10 Temp
drwxrwxrwx 1 root root     122880 2009-02-13 03:01 WINDOWS

/mnt/sdb1:
total 100
drwxr-xr-x   2 root root  4096 2009-02-18 16:45 bin
drwxr-xr-x   3 root root  4096 2009-02-18 16:51 boot
lrwxrwxrwx   1 root root    11 2009-02-18 13:46 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-29 19:04 dev
drwxr-xr-x 125 root root 12288 2009-02-19 13:03 etc
drwxr-xr-x   4 root root  4096 2009-02-19 05:51 home
lrwxrwxrwx   1 root root    33 2009-02-18 16:50 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2009-02-18 13:58 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root 12288 2009-02-18 16:44 lib
drwx------   2 root root 16384 2009-02-18 13:45 lost+found
drwxr-xr-x   7 root root  4096 2009-02-19 12:19 media
drwxr-xr-x   4 root root  4096 2009-02-19 11:52 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 opt
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 proc
drwxr-xr-x  14 root root  4096 2009-02-19 12:56 root
drwxr-xr-x   2 root root  4096 2009-02-18 16:45 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 srv
drwxr-xr-x   2 root root  4096 2008-10-14 09:02 sys
drwxrwxrwt  14 root root  4096 2009-02-19 13:03 tmp
drwxr-xr-x  13 root root  4096 2009-02-18 15:55 usr
drwxr-xr-x  15 root root  4096 2008-10-29 19:12 var
lrwxrwxrwx   1 root root    30 2009-02-18 16:50 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2009-02-18 13:58 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic

---

### Post by caljohnsmith on 2009-02-19
It looks like your drive device names must be changing, because sdb1 now is not the same as the sdb1 that boot script found. How about doing:
```
sudo umount /mnt/sdb1
sudo fdisk -l
```
From the fdisk output, find which is the NTFS partition on one of your 250 GB drives (maybe it is sdc1 now), and then do:
```
sudo mkdir /mnt/sdc1
sudo mount /dev/sdc1 /mnt/sdc1
ls -l /mnt/sdc1
cat /mnt/sdc1/boot.ini
```
But replace sdc1 with the Windows NTFS partition.

---

### Post by wide-load on 2009-02-19
That didn't work.  The first part (umount and fdisk) worked.  When I tried to do the mkdir on sda1 I got an error message that the "file exists".  I didnb't go any farther.

Here is the posting:

greg@Dual-Core6400:~$ sudo umount /mnt/sdb1
[sudo] password for greg: 
greg@Dual-Core6400:~$ sudo umount /mnt/sdb1
umount: /mnt/sdb1: not mounted
greg@Dual-Core6400:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabacc689

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561    7  HPFS/NTFS
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b17e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29646   238131463+  83  Linux
/dev/sdb2           29647       30401     6064537+   5  Extended
/dev/sdb5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x034b034b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2433    19543041    c  W95 FAT32 (LBA)

Disk /dev/sdd: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x855bf51c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       15017   120624021    b  W95 FAT32

Disk /dev/sdi: 1018 MB, 1018691584 bytes
16 heads, 63 sectors/track, 1973 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x37b637b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1        1974      994784+   e  W95 FAT16 (LBA)

Disk /dev/sdj: 8 MB, 8388608 bytes
2 heads, 32 sectors/track, 256 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *           1         256        8176    1  FAT12
greg@Dual-Core6400:~$ sudo mkdir /mnt/sda1
mkdir: cannot create directory `/mnt/sda1': File exists
greg@Dual-Core6400:~$

---

### Post by caljohnsmith on 2009-02-19
OK, so your NTFS partition is now sda1, and it should still be mounted on /mnt/sda1 from the commands you ran previously. So how about doing:
```
cat /mnt/sda1/boot.ini
```

---

### Post by wide-load on 2009-02-19
That didn't work right.  The sudo umount /mnt/sdb1
sudo fdisk -l did.  But when I tried the sudo mkdir /mnt/sda1 I got an error Here is the post:

greg@Dual-Core6400:~$ sudo umount /mnt/sdb1
[sudo] password for greg: 
greg@Dual-Core6400:~$ sudo umount /mnt/sdb1
umount: /mnt/sdb1: not mounted
greg@Dual-Core6400:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabacc689

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561    7  HPFS/NTFS
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b17e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29646   238131463+  83  Linux
/dev/sdb2           29647       30401     6064537+   5  Extended
/dev/sdb5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x034b034b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2433    19543041    c  W95 FAT32 (LBA)

Disk /dev/sdd: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x855bf51c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       15017   120624021    b  W95 FAT32

Disk /dev/sdi: 1018 MB, 1018691584 bytes
16 heads, 63 sectors/track, 1973 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x37b637b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1        1974      994784+   e  W95 FAT16 (LBA)

Disk /dev/sdj: 8 MB, 8388608 bytes
2 heads, 32 sectors/track, 256 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *           1         256        8176    1  FAT12
greg@Dual-Core6400:~$ sudo mkdir /mnt/sda1
mkdir: cannot create directory `/mnt/sda1': File exists
greg@Dual-Core6400:~$ 

I didn't go any farther.

---

### Post by wide-load on 2009-02-19
Here it is.


 cat /mnt/sda1/boot.ini
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(0)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
greg@Dual-Core6400:~$

---

### Post by wide-load on 2009-02-19
Post 13 was a duplicate.  I didn't think it got posted.

---

### Post by caljohnsmith on 2009-02-19
> **wide-load said:**
> 
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)[COLOR="Blue"]rdisk(1)[/COLOR]partition(0)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
```

You need to change both rdisk instances in your boot.ini file to use "0". How about trying again:
```
gksudo gedit /mnt/sda1/boot.ini
```
And change the rdisk shown highlighted in blue above to "rdisk(0)".

---

### Post by wide-load on 2009-02-19
Well, I tied that and it still gives me that double option, when I boot and Select hd2 in the Grub menu.  But at this point I think I'm running after an issue that isn't a big deal.  I can boot into either operating system from the Grub menu and it works fine.  So thanks for your help.  I'll probably go back to menu.lst and remove the references to hd1 hd3 and hd4 that we commented out earlier and leave it at that.

---

### Post by caljohnsmith on 2009-02-19
I just noticed in your boot.ini file that there seems to be a space where there shouldn't be:
```
default=multi(0)disk(0)rdisk(0)partition(1)\WINDO[COLOR="red"]W S[/COLOR]
```
I'm guessing that if you get rid the the space so it is "WINDOWS" instead of "WINDOW S", it will work. But if you don't want to mess with it, that's certainly understandable. Anyway, enjoy your dual-boot setup.

---

