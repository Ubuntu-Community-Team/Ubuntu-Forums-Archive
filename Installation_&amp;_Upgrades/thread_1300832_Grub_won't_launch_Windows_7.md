---
title: "Grub won't launch Windows 7"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by davedosch on 2009-10-25
I bought a new PC that came with Windows 7.  Since I want to keep Windows 7 so I can use iTunes to sync my iPhone, I kept the included drive on the first SATA connection (/dev/sda). I installed another SATA drive (which ended up (/dev/sdd). The DVD drive is (/dev/sdb) and nothing is on (/dev/sdc).  If I tell the bios to but from the first hard drive, Windows 7 boots just fine.  If I tell the bios to boot from the Linux hard drive, Ubuntu 9.10 boots up fine.  If I ask grub (package grub-pc 1.97) to boot from Windows 7 (loader) (on /dev/sda1) I get the following error:

error: no such device: 3694b94794b90a7f

What do I need to do to get grub to boot the Windows 7 partition?

---

### Post by louieb on 2009-10-25
According to the documents I've seen it should be as simple as running.

```
sudo update-grub2
```

---

### Post by davedosch on 2009-10-25
Unfortunately, that doesn't fix the problem.

---

### Post by oldfred on 2009-10-25
Then we need to know what is missing. This script will give us the details:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by davedosch on 2009-10-25
Here's the RESULTS.txt from boot_info_script032.sh:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,927,645,183 1,927,438,336   7 HPFS/NTFS
/dev/sda4       1,927,645,184 1,953,521,663    25,876,480   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34         1,987         1,954 -
/dev/sdb2           1,988 3,859,056,675 3,859,054,688 Linux (usually)
/dev/sdb3   3,859,056,676 3,907,029,134    47,972,459 Linux Swap

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4004 MB, 4004511744 bytes
5 heads, 32 sectors/track, 48883 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17e85f1d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,064     7,821,311     7,813,248   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3694B94794B90A7F" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="66DE80BCDE808651" LABEL="HP" TYPE="ntfs" 
/dev/sda4: UUID="0872C8F172C8E492" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb2: UUID="c2b4cb10-9d85-4a2e-9fbe-425381d175b6" TYPE="ext4" 
/dev/sdb3: UUID="a17fcb13-cd8c-416b-b3fb-fa6ebe40da3b" TYPE="swap" 
/dev/sdc1: LABEL="PATRIOT" UUID="A0D8-61EB" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/davedosch/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=davedosch)
/dev/sdc1 on /media/PATRIOT type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set c2b4cb10-9d85-4a2e-9fbe-425381d175b6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set c2b4cb10-9d85-4a2e-9fbe-425381d175b6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c2b4cb10-9d85-4a2e-9fbe-425381d175b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set c2b4cb10-9d85-4a2e-9fbe-425381d175b6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c2b4cb10-9d85-4a2e-9fbe-425381d175b6 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 3694b94794b90a7f
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
	insmod ntfs
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 0872c8f172c8e492
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=c2b4cb10-9d85-4a2e-9fbe-425381d175b6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=a17fcb13-cd8c-416b-b3fb-fa6ebe40da3b none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 80 22 00 00 00  |............"...|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  01 00 ee fe ff ff 01 00  00 00 af 88 e0 e8 80 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown GPT Partiton Type
4861682149646f6e744e656564454649
Unknown BootLoader  on sdb1

00000000  52 56 be 1b 81 e8 39 01  5e bf f4 81 66 8b 2d 83  |RV....9.^...f.-.|
00000010  7d 08 00 0f 84 e2 00 80  7c ff 00 74 46 66 8b 1d  |}.......|..tFf..|
00000020  66 8b 4d 04 66 31 c0 b0  7f 39 45 08 7f 03 8b 45  |f.M.f1...9E....E|
00000030  08 29 45 08 66 01 05 66  83 55 04 00 c7 04 10 00  |.)E.f..f.U......|
00000040  89 44 02 66 89 5c 08 66  89 4c 0c c7 44 06 00 70  |.D.f.\.f.L..D..p|
00000050  50 c7 44 04 00 00 b4 42  cd 13 0f 82 af 00 bb 00  |P.D....B........|
00000060  70 eb 66 66 8b 45 04 66  09 c0 0f 85 97 00 66 8b  |p.ff.E.f......f.|
00000070  05 66 31 d2 66 f7 34 88  54 0a 66 31 d2 66 f7 74  |.f1.f.4.T.f1.f.t|
00000080  04 88 54 0b 89 44 0c 3b  44 08 7d 79 8b 04 2a 44  |..T..D.;D.}y..*D|
00000090  0a 39 45 08 7f 03 8b 45  08 29 45 08 66 01 05 66  |.9E....E.)E.f..f|
000000a0  83 55 04 00 8a 54 0d c0  e2 06 8a 4c 0a fe c1 08  |.U...T.....L....|
000000b0  d1 8a 6c 0c 5a 52 8a 74  0b 50 bb 00 70 8e c3 31  |..l.ZR.t.P..p..1|
000000c0  db b4 02 cd 13 72 46 8c  c3 8e 45 0a 58 c1 e0 05  |.....rF...E.X...|
000000d0  01 45 0a 60 1e c1 e0 03  89 c1 31 ff 31 f6 8e db  |.E.`......1.1...|
000000e0  fc f3 a5 1f be 23 81 e8  57 00 61 83 7d 08 00 0f  |.....#..W.a.}...|
000000f0  85 24 ff 83 ef 0c e9 16  ff be 25 81 e8 42 00 5a  |.$........%..B.Z|
00000100  ea 00 82 00 00 be 28 81  e8 36 00 eb 06 be 2d 81  |......(..6....-.|
00000110  e8 2e 00 be 32 81 e8 28  00 eb fe 6c 6f 61 64 69  |....2..(...loadi|
00000120  6e 67 00 2e 00 0d 0a 00  47 65 6f 6d 00 52 65 61  |ng......Geom.Rea|
00000130  64 00 20 45 72 72 6f 72  00 bb 01 00 b4 0e cd 10  |d. Error........|
00000140  46 8a 04 3c 00 75 f2 c3  00 00 00 00 00 00 00 00  |F..<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 23 00 00 00  00 00 00 00 30 00 20 08  |....#.......0. .|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh sdi

---

### Post by oldfred on 2009-10-25
It seems the script does not identify grub2 correctly but I assume that is what is in the MBR of sdb.

If you change the BIOS boot order so sdb boots first, can you boot ok into ubuntu? (windows will not work as now that is the second drive).

If then you run the sudo update-grub2 it should add in the mapping command to make windows work from the second drive.

---

### Post by oldfred on 2009-10-25
The GPT and GUID comments in the script indicate that the drive was configured for an Apple compter or windows server. That may be causing further problems, I am not familiar with those issues.

---

### Post by Mark Phelps on 2009-10-25
Presuming that you're booting from your Ubuntu drive, the simple problem is that the 30_OS-prober entries for Windows 7 point to the wrong drive.  When the Ubuntu drive is the boot drive, the MS Windows drive is really hd1, not hd0.

Using legacy GRUB, you would have changed your menu.lst entries to be the following:
title    Windows 7 Boot Loader
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

How you get these changes (presuming they work) into the 30_OS-prober file I do NOT know.  Not an expert on GRUB2.

---

### Post by davedosch on 2009-10-28
OK, couldn't get GRUB to configure to boot Windows 7, so I went in and changed the order of the drives by changing the SATA connectors around, re-ran grub-setup but still get that "error: no such device: 3694b94794b90a7f" when I try to boot Windows 7 from grub.

The new RESULT.txt:
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34         1,987         1,954 -
/dev/sda2           1,988 3,859,056,675 3,859,054,688 Linux (usually)
/dev/sda3   3,859,056,676 3,907,029,134    47,972,459 Linux Swap

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848 1,927,645,183 1,927,438,336   7 HPFS/NTFS
/dev/sdb4       1,927,645,184 1,953,521,663    25,876,480   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="c2b4cb10-9d85-4a2e-9fbe-425381d175b6" TYPE="ext4" 
/dev/sda3: UUID="a17fcb13-cd8c-416b-b3fb-fa6ebe40da3b" TYPE="swap" 
/dev/sdb1: UUID="3694B94794B90A7F" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sdb2: UUID="66DE80BCDE808651" LABEL="HP" TYPE="ntfs" 
/dev/sdb4: UUID="0872C8F172C8E492" LABEL="FACTORY_IMAGE" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/davedosch/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=davedosch)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set c2b4cb10-9d85-4a2e-9fbe-425381d175b6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c2b4cb10-9d85-4a2e-9fbe-425381d175b6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c2b4cb10-9d85-4a2e-9fbe-425381d175b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c2b4cb10-9d85-4a2e-9fbe-425381d175b6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c2b4cb10-9d85-4a2e-9fbe-425381d175b6 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3694b94794b90a7f
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb4)" {
	insmod ntfs
	set root=(hd1,4)
	search --no-floppy --fs-uuid --set 0872c8f172c8e492
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=c2b4cb10-9d85-4a2e-9fbe-425381d175b6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=a17fcb13-cd8c-416b-b3fb-fa6ebe40da3b none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 80 22 00 00 00  |............"...|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  01 00 ee fe ff ff 01 00  00 00 af 88 e0 e8 80 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown GPT Partiton Type
4861682149646f6e744e656564454649
Unknown BootLoader  on sda1

00000000  52 56 be 1b 81 e8 39 01  5e bf f4 81 66 8b 2d 83  |RV....9.^...f.-.|
00000010  7d 08 00 0f 84 e2 00 80  7c ff 00 74 46 66 8b 1d  |}.......|..tFf..|
00000020  66 8b 4d 04 66 31 c0 b0  7f 39 45 08 7f 03 8b 45  |f.M.f1...9E....E|
00000030  08 29 45 08 66 01 05 66  83 55 04 00 c7 04 10 00  |.)E.f..f.U......|
00000040  89 44 02 66 89 5c 08 66  89 4c 0c c7 44 06 00 70  |.D.f.\.f.L..D..p|
00000050  50 c7 44 04 00 00 b4 42  cd 13 0f 82 af 00 bb 00  |P.D....B........|
00000060  70 eb 66 66 8b 45 04 66  09 c0 0f 85 97 00 66 8b  |p.ff.E.f......f.|
00000070  05 66 31 d2 66 f7 34 88  54 0a 66 31 d2 66 f7 74  |.f1.f.4.T.f1.f.t|
00000080  04 88 54 0b 89 44 0c 3b  44 08 7d 79 8b 04 2a 44  |..T..D.;D.}y..*D|
00000090  0a 39 45 08 7f 03 8b 45  08 29 45 08 66 01 05 66  |.9E....E.)E.f..f|
000000a0  83 55 04 00 8a 54 0d c0  e2 06 8a 4c 0a fe c1 08  |.U...T.....L....|
000000b0  d1 8a 6c 0c 5a 52 8a 74  0b 50 bb 00 70 8e c3 31  |..l.ZR.t.P..p..1|
000000c0  db b4 02 cd 13 72 46 8c  c3 8e 45 0a 58 c1 e0 05  |.....rF...E.X...|
000000d0  01 45 0a 60 1e c1 e0 03  89 c1 31 ff 31 f6 8e db  |.E.`......1.1...|
000000e0  fc f3 a5 1f be 23 81 e8  57 00 61 83 7d 08 00 0f  |.....#..W.a.}...|
000000f0  85 24 ff 83 ef 0c e9 16  ff be 25 81 e8 42 00 5a  |.$........%..B.Z|
00000100  ea 00 82 00 00 be 28 81  e8 36 00 eb 06 be 2d 81  |......(..6....-.|
00000110  e8 2e 00 be 32 81 e8 28  00 eb fe 6c 6f 61 64 69  |....2..(...loadi|
00000120  6e 67 00 2e 00 0d 0a 00  47 65 6f 6d 00 52 65 61  |ng......Geom.Rea|
00000130  64 00 20 45 72 72 6f 72  00 bb 01 00 b4 0e cd 10  |d. Error........|
00000140  46 8a 04 3c 00 75 f2 c3  00 00 00 00 00 00 00 00  |F..<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 23 00 00 00  00 00 00 00 30 00 20 08  |....#.......0. .|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg sdh

---

### Post by oldfred on 2009-10-28
Now that windows is on the second drive you need the map commands like Mark Phelps said except for grub2 map has changed to drivemap and is one line.

Since it is not finding the command correctly I would copy your current windows entries for both wind7 & Vista as I am not sure which is correct into the /etc/grub.d/40_custom file and manually add the drivemap command.
I have seen two versions of drivemap
drivemap -s (hd0) ${root}  # not sure if it should be (hd1) ${root}
drivemap -s (hd1) (hd0)

So copy entries like this  with one or the other drivemap commands, make sure the file is executable and then run the sudo update-grub2:

```
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3694b94794b90a7f
drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb4)" {
    insmod ntfs
    set root=(hd1,4)
    search --no-floppy --fs-uuid --set 0872c8f172c8e492
drivemap -s (hd0) ${root}
    chainloader +1
}
```

---

