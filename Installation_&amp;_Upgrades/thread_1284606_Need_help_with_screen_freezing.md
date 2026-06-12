---
title: "Need help with screen freezing"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by lemon_lime123 on 2009-10-06
Installed 9.04 on my desktop, seemed to work fine. Restarted it and it froze at the login screen. Tried it a couple more times and now it freezes at the spinning cirsor. Its a Compaq with a pentium 4, it should work, 1.24GB RAM

Any Suggestions?

Tried this [page]("http://pramodrt.wordpress.com/2009/05/23/ubuntu-9-04-kernel-panic-problem/") which the person had the almost the same problem as i do, followed the instructions, no go.
Also sometimes I get up to the first drumbeat sound, sometimes just the spinning cursor, sometimes a black screen with a white password box.

EDIT: Tried updating to kernal 2.6.30.3, no go

---

### Post by rreese6 on 2009-10-07
Does this problem get worse the longer the Computer is turned on?

If so it might be that your computer needs to have the dust cleaned out of it. another issue might be that you had a bad installation CD . dod you run the "Check CD Media"?

---

### Post by lemon_lime123 on 2009-10-07
I cleaned out the dust not too long ago, maybe like a week or two, but I can do it again to make sure.  I had originally tried using CD-Rom to install but the LiveCD would not work and the alternate CD failed the integrity test every time I burned it. So I re-downloaded the Alternate cd, ran an MD5 Sum, which it passed, and made a USB startup disk off another Ubuntu computer.

---

### Post by lemon_lime123 on 2009-10-11
Update:  This morning my mom turned on the computer and left it there. It went into Ubuntu and took me into the login screen without freezing. Cautiously, I entered my username and password, and it logged in- for the first time. I tried to connect to my network, and it froze, like it did before. Tried restarting, back to my original problem.

---

### Post by rreese6 on 2009-10-11
Could be a memory issue. if not heat. (I am sure you made sure that all your fans are operational (running). Try to boot the system with the LiveCD and run the memory test. let it run as long as it can. and if the system freezes, I would suggest powering down, removing all cards and clean edges by rubbing gold contacts with the blank side of a business card or 3x5 cards..paper will work but use small pieces so you don,t build up static. then reinstall cards as try again.
if you have a memory error. eliminate all memory cards except one (unless you only have one) and try one card at a time to find the bad one. if you only have one card then replace it.
Also I have seen where the CPU had overheated once and only partially works afterwords. especially if the thermal compound had dried out between the cpu and heatsink.
his really doesn't seem like a software issue, but it might be. Try an older version of Ubuntu from LiveCD boot, if after checking all the hardware showed nothing

---

### Post by lemon_lime123 on 2009-10-12
mem test was fine, but at the advice of another person, I installed 9.10 manually, only to find that now the system doesn't freeze, but I'm stuck in a root shell prompt. Worse, XP doesn't show up in Grub anymore, and i didn't overwrite any existing partitions, I just used unallocated space. I really stuck in a pickle now.

---

### Post by rreese6 on 2009-10-12
It seems like you know have two Linux installations one that boot only in the shell (root prompt) usually used for making non-gui server installations. and then you have Windows and a GUI Linux. Basically 3 OS's installed.
Let's get a snapshot of what you have going on now.

You need to download the Boot Info Script and post the info from its output file (Readme.txt) here (Be sure to click the '#" symbol before pasting so that the output is in a scrollable window in your post (makes it easier to read. 

1. Boot up with LiveCD. Once you are on the Desktop, go to this link and download:
```
[Download Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/")
```
This Script will gather your current configuration and make a report.
This gives us a better idea of what your problem is and how to fix it.

2. Open up terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will make a file called "Readme.txt" on your desktop.

3. Post the contents of that file here.

---

### Post by theozzlives on 2009-10-12
As far as the GRUB menu, ```
sudo update-grub
```should fix that. It's been an issue in GRUB2 for awhile now.

---

### Post by rreese6 on 2009-10-12
> **theozzlives said:**
> As far as the GRUB menu, ```
sudo update-grub
```should fix that. It's been an issue in GRUB2 for awhile now.

His Original problem is not the "extra installation" so we relly don't want to update grub to include "the fix" he got from somewhere else.
I am in the opinion that he should remove the last install and repair the original dual boot. seems like a video card or Hardware issue.

---

### Post by lemon_lime123 on 2009-10-12
I tried booting from the LiveCD.
All I got was
```

Starting early crypto disks....                                                     [OK]
Starting remaining crypto disks...                                                  [OK]
_
```The cursor is blinking but nothing happens after that.



I can try running the Boot Information Script off a USB, in the root shell, how does that sound?

---

### Post by rreese6 on 2009-10-12
try it.

---

### Post by lemon_lime123 on 2009-10-13
I mounted my USB on it, and ran it from there, so here is the txt file. ```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Recovery:Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf84ef84e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    13,865,039    13,864,977   b W95 FAT32
/dev/sda2    *     15,256,080   201,670,559   186,414,480   7 HPFS/NTFS
/dev/sda3         201,670,560   234,435,599    32,765,040   5 Extended
/dev/sda5         201,670,623   232,968,959    31,298,337  83 Linux
/dev/sda6         232,969,023   234,435,599     1,466,577  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4025 MB, 4025810432 bytes
114 heads, 7 sectors/track, 9853 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cdf55

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              1     7,862,910     7,862,910   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PRESARIO_RP" UUID="3F46-666D" TYPE="vfat" 
/dev/sda2: UUID="346059A060596A1E" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda5: UUID="82d5e0ec-89cd-40b9-aa7d-ef5a8c1e368c" TYPE="ext4" 
/dev/sda6: UUID="25be8e27-3ccb-4581-a543-572b392cdd40" TYPE="swap" 
/dev/sdb1: UUID="08F0-0DC2" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
none on /proc type proc (rw)
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
/dev/sdb1 on /media/external type vfat (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 82d5e0ec-89cd-40b9-aa7d-ef5a8c1e368c
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
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 82d5e0ec-89cd-40b9-aa7d-ef5a8c1e368c
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=82d5e0ec-89cd-40b9-aa7d-ef5a8c1e368c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 82d5e0ec-89cd-40b9-aa7d-ef5a8c1e368c
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=82d5e0ec-89cd-40b9-aa7d-ef5a8c1e368c ro single 
    initrd    /boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3f46-666d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 346059a060596a1e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=82d5e0ec-89cd-40b9-aa7d-ef5a8c1e368c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=25be8e27-3ccb-4581-a543-572b392cdd40 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 103.2GB: boot/grub/grub.cfg
 103.2GB: boot/initrd.img-2.6.31-11-generic
 103.2GB: boot/vmlinuz-2.6.31-11-generic
 103.2GB: initrd.img
 103.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 00 02 8e d7 bc  00 7a bb a0 07 8b ce 8e  |.c.......z......|
00000010  db 8e c3 fc f3 a4 ea 52  00 a0 07 10 00 01 00 00  |.......R........|
00000020  7a 00 00 00 00 00 00 00  00 00 00 8b f5 b1 04 38  |z..............8|
00000030  64 04 74 0d 38 44 04 74  08 83 c6 10 e2 f1 03 02  |d.t.8D.t........|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  4e f8 4e f8 00 00 00 01  |...<.u..N.N.....|
000001c0  01 00 0b ef ff 94 3f 00  00 00 11 90 d3 00 80 00  |......?.........|
000001d0  c1 f1 07 ef ff ff 10 ca  e8 00 90 75 1c 0b 00 ef  |...........u....|
000001e0  ff ff 05 ef ff ff a0 3f  05 0c 70 f4 f3 01 00 00  |.......?..p.....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Just thinking maybe u=I accidentally  installed downloaded the server software instead of the desktop software.

---

### Post by lemon_lime123 on 2009-10-15
Update: updated grub, deleted 9.10 partition, installed 9.04. Now i can boot Xp again and I have 9.04 and I'm back to my original problem. When I try to boot Ubuntu, the screen stops at the spinning cursor. I already tried using just one stick of RAM, neither of them fixed the problem. At this point, I don't know what to do. Any help here?

---

