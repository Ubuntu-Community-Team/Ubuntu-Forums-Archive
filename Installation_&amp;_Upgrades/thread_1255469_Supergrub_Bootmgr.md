---
title: "Supergrub Bootmgr"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by bobby2000 on 2009-09-01
hey, installed ubuntu's netbook distro on a dell 10v all was working fine, restarted at now getting error 22. downloaded supergrub and put onto a usb however the copies i've downloaded don't have a bootmgr file on them and so i'm getting "bootmgr is missing" when booting from it.

Ideas?

Thanks

---

### Post by presence1960 on 2009-09-01
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bobby2000 on 2009-09-01
ok, i'm gonna have to redownload the disk though as my external HD crashed and died this morning. Best one to use?

---

### Post by bobby2000 on 2009-09-01
now downloading remix disk

---

### Post by bobby2000 on 2009-09-01
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdc

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa42d04a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920   207,339,896   207,257,977   7 HPFS/NTFS
/dev/sda3         207,339,897   312,576,704   105,236,808   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8015 MB, 8015314944 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ef631df

Partition  Boot         Start           End          Size  Id System

/dev/sdc1     ? 2,112,536,064 4,071,284,395 1,958,748,332  66 Unknown
/dev/sdc2     ? 3,449,352,939 7,393,689,600 3,944,336,662   7 HPFS/NTFS
/dev/sdc3     ? 3,279,813,678 5,233,273,711 1,953,460,034  7d Unknown
/dev/sdc4     ? 4,179,361,792 4,187,684,891     8,323,100  6f Unknown

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc2
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc2 overlaps with /dev/sdc4
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc3 overlaps with /dev/sdc4
/dev/sdc4 ends after the last sector of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="E07E631E7E62ED2A" LABEL="OS" TYPE="ntfs" 
/dev/sda3: UUID="D65CA0BF5CA09BAD" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc: UUID="49ED-21FF" TYPE="vfat" 

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
/dev/sdc on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 08 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  c0 96 1d 00 62 07 00 00  00 00 00 00 02 00 00 00  |....b...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ff 21 ed 49 20  20 20 20 20 20 20 20 20  |..).!.I         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c0 8e d0  |  FAT32   ..1...|
00000060  bc b4 7b 06 57 8e c0 b9  08 00 bf b4 7b f3 a5 8e  |..{.W.......{...|
00000070  d8 bb 78 00 0f b4 37 0f  a0 56 88 16 21 c7 20 d2  |..x...7..V..!. .|
00000080  78 15 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |x....?.G..d....||
00000090  88 4d f8 cd 13 eb 27 f6  45 f0 7f 75 08 66 8b 45  |.M....'.E..u.f.E|
000000a0  f8 66 a3 1c 7c b4 08 cd  13 72 13 20 e4 75 0f c1  |.f..|....r. .u..|
000000b0  ea 08 42 89 16 1a 7c 83  e1 3f 89 0e 18 7c fb bb  |..B...|..?...|..|
000000c0  aa 55 b4 41 8a 16 21 c7  cd 13 72 10 81 fb 55 aa  |.U.A..!...r...U.|
000000d0  75 0a f6 c1 01 74 05 c6  06 05 7d 00 66 a1 f8 7d  |u....t....}.f..}|
000000e0  bb 00 7e e8 10 00 66 81  3e 2c 7e e8 e1 06 77 0f  |..~...f.>,~...w.|
000000f0  85 c6 00 e9 42 02 bd 01  00 66 03 06 1c 7c 66 31  |....B....f...|f1|
00000100  d2 e9 00 00 eb 4f 55 e8  d5 00 66 0f b7 fd b9 10  |.....OU...f.....|
00000110  00 66 52 66 50 06 53 57  6a 10 89 e6 66 60 8a 16  |.fRfP.SWj...f`..|
00000120  21 c7 1e 16 1f b4 42 cd  13 1f 66 61 8d 64 10 72  |!.....B...fa.d.r|
00000130  10 5d 66 01 f8 29 fd c1  e7 09 01 fb 21 ed 75 c6  |.]f..)......!.u.|
00000140  c3 66 60 31 c0 8a 16 21  c7 cd 13 66 61 e2 c2 c6  |.f`1...!...fa...|
00000150  06 05 7d 4f 5d 66 52 66  50 55 53 66 0f b7 36 18  |..}O]fRfPUSf..6.|
00000160  7c 66 0f b7 3e 1a 7c 66  f7 f6 31 c9 87 ca 66 f7  ||f..>.|f..1...f.|
00000170  f7 e8 6b 00 29 ce 39 f5  76 02 89 f5 c0 e4 06 41  |..k.).9.v......A|
00000180  08 e1 88 c5 88 d6 8a 16  21 c7 95 b4 02 bd 10 00  |........!.......|
00000190  66 60 cd 13 66 61 72 17  66 0f b6 c8 c1 e0 09 5b  |f`..far.f......[|
000001a0  01 c3 5d 66 58 66 5a 66  01 c8 29 cd 75 a7 c3 4d  |..]fXfZf..).u..M|
000001b0  75 de 95 d1 2e fc 7d 75  df 31 f6 8e d6 bc b0 7b  |u.....}u.1.....{|
000001c0  8e de 66 8f 06 78 00 be  ea 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001d0  0e bb 07 00 cd 10 eb f2  98 cd 16 cd 19 eb fe 3b  |...............;|
000001e0  2e fc 7d 76 04 8b 2e fc  7d c3 42 6f 6f 74 20 65  |..}v....}.Boot e|
000001f0  72 72 6f 72 0d 0a 00 00  1c f9 1c 00 7f 00 55 aa  |rror..........U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3


Unknown BootLoader  on sdc4



=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory

---

### Post by presence1960 on 2009-09-01
you have no Ubuntu partitions. your GRUB is installed in MBR of sda and looks to sda5 for menu.lst. 
it must have been there at one time or it couldn't point to a non-existant partition. Were you playing around with Partition Editor (gparted)?

You are going to have to reinstall Ubuntu. 
You get error 22 because there is no partition with menu.lst where GRUB expects to find one. it must have been deleted and that did not happen on it's own or by installing a program.

Whatever sdc is that disk is a mess. you have problems on that disk too. partitions overlapping each other on that disk. I suggest saving anything you want from sdc and format the whole disk and set up new partitions.

---

### Post by bobby2000 on 2009-09-01
ok now reinstalling remix, i'll post how it goes.

Thanks guys

---

