---
title: "GRUB loading. 4ever."
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by vickertj on 2009-10-23
OK, so I started with the following dual-boot config:
1.) 2 hard drives (sda and sdb). 
2.) windows xp on sda
3.) ubuntu 9.04 on sdb
4.) GRUB as a boot loader in MBR of hd0

this worked fine and dandy. All I did is install 9.10 over sdb using the RC LiveCD, and now I can't boot anything. Thanks GRUB2! It gets through the bios post stuff and then says "GRUB loading." and nothing happens. Any advice? All I could find seemed to be outdated. Already tried reinstalling. 

Advice appreciated. I miss old grub.

---

### Post by presence1960 on 2009-10-23
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by vickertj on 2009-10-23
OK, here we go (thanks for the quick response, btw). As you see below I have sdb divvied up into /, /home, and swap; sda contains the dell utility partition in addition to windows xp...None of this was a problem with Jaunty.
 

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   488,279,609   488,183,220   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f933

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   292,961,339   292,961,277  83 Linux
/dev/sdb2         292,961,340 1,953,520,064 1,660,558,725   5 Extended
/dev/sdb5         292,961,403   308,592,584    15,631,182  82 Linux swap / Solaris
/dev/sdb6         308,592,648 1,953,520,064 1,644,927,417  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0B09" TYPE="vfat" 
/dev/sda2: UUID="0248424448423727" TYPE="ntfs" 
/dev/sdb1: UUID="c5767914-e7ae-4e4d-8bd8-250dfb057c2a" TYPE="ext4" 
/dev/sdb5: UUID="b3ad5227-e93b-43b6-8394-ad665745f064" TYPE="swap" 
/dev/sdb6: UUID="7b713a11-d7e2-49c7-9ee2-e4fcd7a5b783" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb6 on /media/7b713a11-d7e2-49c7-9ee2-e4fcd7a5b783 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1 on /media/c5767914-e7ae-4e4d-8bd8-250dfb057c2a type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set c5767914-e7ae-4e4d-8bd8-250dfb057c2a
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c5767914-e7ae-4e4d-8bd8-250dfb057c2a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c5767914-e7ae-4e4d-8bd8-250dfb057c2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c5767914-e7ae-4e4d-8bd8-250dfb057c2a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c5767914-e7ae-4e4d-8bd8-250dfb057c2a ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 07d6-0b09
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0248424448423727
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=c5767914-e7ae-4e4d-8bd8-250dfb057c2a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=7b713a11-d7e2-49c7-9ee2-e4fcd7a5b783 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=b3ad5227-e93b-43b6-8394-ad665745f064 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 8e d8 8e c0 8e  d0 bc 00 7c fb fc 89 e6  |.c.........|....|
00000010  bf 00 06 b9 00 01 f3 a5  ea 1d 06 00 00 88 16 00  |................|
00000020  08 b4 08 cd 13 31 c0 88  f0 40 a3 ec 06 80 e1 3f  |.....1...@.....?|
00000030  88 0e ee 06 be be 07 31  c0 b9 04 00 f6 04 03 02  |.......1........|
00000040  80 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  16 23 ab 41 00 00 00 01  |...<.u...#.A....|
000001c0  01 00 de fe 3f 05 3f 00  00 00 47 78 01 00 80 00  |....?.?...Gx....|
000001d0  01 06 07 fe ff ff 86 78  01 00 b4 15 19 1d 00 00  |.......x........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by presence1960 on 2009-10-23
you do not have GRUB installed to the MBR of either disk. I am not familiar with GRUB 2 which is what 9.10 uses. There is a forum for 9.10. Maybe you can get help there to install GRUB 2 to MBR. Unfortunately I am not familiar with GRUB 2 and it's commands yet. 

But that is why your machine is not booting. You need to put GRUB on MBR. I would put it on MBR of sdb then set sdb as first boot in hard disk boot order in BIOS. This will bring up GRUB when you boot.

P.S. what happened to the windows bootloader on sda?

---

### Post by vickertj on 2009-10-24
Thanks, I reinstalled and selected /dev/sdb instead of the default. It seems to be working now if I tell the BIOS to boot from SDB, and even detects XP (although I haven't tested that it boots OK yet). I don't understand why the default selection did not install it into the MBR of sda, since that is what it did when I installed 9.04...Anyways, thanks for pointing me to the solution.

---

### Post by presence1960 on 2009-10-24
> **vickertj said:**
> Thanks, I reinstalled and selected /dev/sdb instead of the default. It seems to be working now if I tell the BIOS to boot from SDB, and even detects XP (although I haven't tested that it boots OK yet). I don't understand why the default selection did not install it into the MBR of sda, since that is what it did when I installed 9.04...Anyways, thanks for pointing me to the solution.

you should be good to go now, I would go into BIOS and set sdb as first in the hard disk boot order that way you don't have to keep going into BIOS at boot.

If you have problems with windows post back.

---

