---
title: "Ubuntu 9.10 raid 0 grub windows 7 and other"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by syryo on 2009-11-12
I am not a smart Ubunter, neither Gruber.
I have three disks: two are fake RAID 0 configured. 
I have successfully installed Ubuntu 9.10 (using LIVE CD) after I had already installed XP and Windows 7.
Ubuntu has installed Grub0.97 in MBR of raid 0.

When the PC boots, Grub shows a menu (1st menu) and let me select among Ubuntu (3 items created by LIVE CD) and Windows (item that I added in menu.lst).

When I start Ubuntu it starts OK.

When I start Windows, a menu is shown; this is the 'old' menu that I had before installing Ubuntu, this is the menu created by Windows 7.
In this 2nd menu there is also the item Previous Windows because, as I told, on my PC there is also XP partition. So if I select this item I am shown a 3rd menu (from boot.ini) where I can choose between XP pro and XP x64.

My question is: how can I have only 1 menu or at least 2 menus?

Here is the results.txt.
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdc7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x258c258b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,471,334    31,471,272   7 HPFS/NTFS
/dev/sda2          31,471,335 1,153,483,064 1,122,011,730   5 Extended
Invalid MBR Signature found
Empty Partition
/dev/sda3       1,153,483,065 1,196,489,069    43,006,005  83 Linux
/dev/sda4       1,196,489,070 1,250,274,689    53,785,620   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa15f48fc

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1     ? 2,035,506,150 6,101,875,332 4,066,369,183  83 Linux
/dev/sdb2     ? 1,138,666,734 5,296,893,256 4,158,226,523  2f Unknown
/dev/sdb3     ? 3,556,899,272 6,744,417,604 3,187,518,333  4f QNX4.x 3rd part
/dev/sdb4     ? 4,205,887,270 6,171,956,492 1,966,069,223  18 AST SmartSleep

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb1 overlaps with /dev/sdb3
/dev/sdb1 overlaps with /dev/sdb4
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00008ac4

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    52,436,159    52,436,097   7 HPFS/NTFS
/dev/sdc2          79,730,595 1,953,520,064 1,873,789,470   5 Extended
/dev/sdc5         104,872,383   157,308,479    52,436,097   7 HPFS/NTFS
/dev/sdc6         157,308,543   209,744,639    52,436,097   7 HPFS/NTFS
/dev/sdc7         209,744,703 1,953,520,064 1,743,775,362   7 HPFS/NTFS
/dev/sdc3    *     52,436,160    79,730,594    27,294,435   7 HPFS/NTFS
/dev/sdc4          79,730,658   104,872,319    25,141,662   7 HPFS/NTFS

/dev/sdc2 overlaps with /dev/sdc4

blkid -c /dev/null: ____________________________________________________________

/dev/sda: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc1: UUID="4491F7DB4A0A1F90" LABEL="win7Pro32Ita" TYPE="ntfs" 
/dev/sdc3: UUID="5E605825605805E5" LABEL="Xp64ProIta" TYPE="ntfs" 
/dev/sdc4: UUID="569C9DF99C9DD439" LABEL="Xp64Eng" TYPE="ntfs" 
/dev/sdc5: UUID="81302B4D129CFA4A" LABEL="win7Pro64Ita" TYPE="ntfs" 
/dev/sdc6: UUID="92F6061BF605FFE9" LABEL="Win7ita64" TYPE="ntfs" 
/dev/sdc7: UUID="52F64E8AF64E6E73" LABEL="BKUP" TYPE="ntfs" 
/dev/mapper/isw_bihfegibga_Volume01: UUID="043C0ACD3C0ABA26" LABEL="WinXpPro32" TYPE="ntfs" 
/dev/mapper/isw_bihfegibga_Volume03: UUID="dd2d3071-83af-4f83-9cf2-801a3b459a14" TYPE="ext3" 
/dev/mapper/isw_bihfegibga_Volume04: UUID="92F6061BF605FFE9" LABEL="Win7Ult64Ita" TYPE="ntfs" 
/dev/mapper/isw_bihfegibga_Volume05: UUID="BAA676F2A31B7D36" LABEL="DATI" TYPE="ntfs" 
/dev/mapper/isw_bihfegibga_Volume06: UUID="AE8C4E521033AA06" LABEL="ALTRO" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/mapper/isw_bihfegibga_Volume03 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/syryo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=syryo)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=syryo)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  c6 9d a6 83 78 cf 72 c9  d5 75 ce 37 9d cf 64 bd  |....x.r..u.7..d.|
00000010  e7 9b ef e3 ee 36 58 78  e5 a9 8e fc 5a 65 16 cd  |.....6Xx....Ze..|
00000020  79 d7 dd 92 37 b3 6b 37  7c 78 73 0e 87 2c 77 02  |y...7.k7|xs..,w.|
00000030  a3 07 14 1f c5 0f d2 d5  6a a9 80 3f e0 25 76 1f  |........j..?.%v.|
00000040  6f 7e ff b1 de cc f8 77  3d 94 7f f8 11 08 df d5  |o~.....w=.......|
00000050  cf d5 94 d4 56 41 26 fe  f7 15 3f c1 ab f9 41 95  |....VA&...?...A.|
00000060  81 aa 46 fe c0 6a 1f 16  4f d0 81 54 a3 a7 d4 69  |..F..j..O..T...i|
00000070  61 e6 1a e9 3b f6 f1 2a  1e 9f 13 cc 19 16 ba af  |a...;..*........|
00000080  10 0d bf 16 57 d0 81 95  01 20 d6 a1 16 9f f3 3f  |....W.... .....?|
00000090  6c 3f 7f d2 d7 00 5a df  9f 8f d5 ff f3 58 c2 df  |l?....Z......X..|
000000a0  fb 9f 83 b2 52 29 70 a7  19 1f b7 2e 5b 19 26 5d  |....R)p.....[.&]|
000000b0  f9 96 5c ae b1 79 1a b9  17 e7 60 1e e4 45 6a 21  |..\..y....`..Ej!|
000000c0  1b d7 2b bf 30 9b 62 df  c0 e2 7a 68 85 15 1a f8  |..+.0.b...zh....|
000000d0  d2 fe 0d 42 7c 53 c5 bb  f4 b7 8b 4a 8a a2 f4 de  |...B|S.....J....|
000000e0  e0 88 e5 5b 0b f9 6e fa  f2 dc 1f ae 91 9b c5 77  |...[..n........w|
000000f0  1f df f5 57 f4 f0 db 58  58 39 5b f5 79 25 65 ff  |...W...XX9[.y%e.|
00000100  ea 61 6b 5c db 8f ea b9  c3 d6 f0 59 1f f9 ce 5a  |.ak\.......Y...Z|
00000110  70 59 1b dc cf a3 cc 5e  dd d9 ba 68 70 f7 8f 3e  |pY.....^...hp..>|
00000120  bd a9 57 c5 79 eb 65 3e  bd f3 03 3f f4 bc dc 2f  |..W.y.e>...?.../|
00000130  14 2d 81 93 f7 98 44 72  74 f5 56 ba 77 65 ff ac  |.-....Drt.V.we..|
00000140  d5 57 53 5f 42 b8 76 c9  d8 7a 62 a7 3b eb 2e 88  |.WS_B.v..zb.;...|
00000150  26 2b 5b e6 7d 4a 5b af  d1 5d f4 c5 7a 6c 17 0d  |&+[.}J[..]..zl..|
00000160  ff 1d c2 bb e2 ac d9 76  1d 27 3b 07 9c 67 d7 b4  |.......v.';..g..|
00000170  9d 72 cc f6 52 6e 99 27  6b ca a3 51 ab e5 79 dd  |.r..Rn.'k..Q..y.|
00000180  ad f9 7d 1d 60 c3 9f b4  b1 0c 86 41 a7 cf c2 74  |..}.`......A...t|
00000190  dd 3d 9f f1 48 a3 b0 df  aa cd 2c 6d be f9 5f ad  |.=..H.....,m.._.|
000001a0  9d 82 98 37 b6 f4 b9 37  63 1b 2b 9f ac 59 da eb  |...7...7c.+..Y..|
000001b0  2f 38 dd da 7b 2a c3 ce  fc 48 5f a1 e4 03 3f 97  |/8..{*...H_...?.|
000001c0  07 59 83 29 71 ed e6 5b  53 79 9f de 5f f2 51 87  |.Y.)q..[Sy.._.Q.|
000001d0  f0 17 2f c7 1f b5 ee ac  de 43 5b 80 d9 f7 af b2  |../......C[.....|
000001e0  21 f1 4f f5 35 fa c8 f9  01 d4 7d ab fd bd f7 f6  |!.O.5.....}.....|
000001f0  40 e8 18 80 bf be 26 bf  b0 fa e7 d5 2f 75 45 18  |@.....&...../uE.|
00000200

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

---

### Post by syryo on 2009-11-12
I forgot to attach the menu.lst:

title                 Windows
rootnoverify (hd0,0)   # use the correct partition for Windows, of course
makeactive
chainloader +1

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_bihfegibga_Volume03 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_bihfegibga_Volume03 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin

---

