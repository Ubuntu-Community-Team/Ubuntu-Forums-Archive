---
title: "Cannot Boot after Karmic install, Grub Error 15"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by gibblegobble on 2009-10-29
Ok, so I installed karmic, however I haven't actually been able to boot up. what my computer tells me is this.

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15
```

I've tried reinstalling, Karmic, I've tried reinstalling grub2 but none of that seems to work - I've read that your not supposed to edit grub.cfg but as far as I can tell everything is right in there as it should be. I ran this script that gave me some information, but I am not sure what to do with it so here it is.

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Grub0.97 is installed in the MBR of /dev/sde and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdf
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13459d3c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,000,924    20,000,862  83 Linux
/dev/sda2          20,000,925   490,223,474   470,222,550  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000456e8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031b30

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282  83 Linux


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009207b

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    41,945,714    41,945,652  83 Linux
/dev/sdd2          41,945,715   625,137,344   583,191,630  83 Linux


Drive sde: _____________________________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37e937e9

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   488,392,064   488,392,002  83 Linux


Drive sdf: _____________________________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000715ba

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63     4,000,184     4,000,122  82 Linux swap / Solaris
/dev/sdf2           4,000,185   976,768,064   972,767,880  83 Linux


Drive sdg: _____________________________________________________________________

Disk /dev/sdg: 16.1 GB, 16131293184 bytes
25 heads, 25 sectors/track, 50410 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               2,048    31,506,431    31,504,384   c W95 FAT32 (LBA)

/dev/sdg1 ends after the last cylinder of /dev/sdg

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2f3d7d5b-37f1-44ba-bdcf-a09ddaa253fb" TYPE="ext4" 
/dev/sda2: UUID="3b78e1f7-5070-444c-8696-719a3e7f6cb1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="Gamma" UUID="8edb1624-f68b-4025-9634-7995c658c174" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="Delta" UUID="44debf5a-88c7-405b-a802-d2e7ff6fe595" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sde1: LABEL="Alpha" UUID="21bcf72f-62bb-4569-8396-6e54f82f4734" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdf1: UUID="189340b7-f668-4bd7-ace8-b59c7b859110" TYPE="swap" 
/dev/sdf2: LABEL="Beta" UUID="de8ea70e-2687-440f-b719-774a8d6ffb85" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="29192e7b-6738-4fb9-9c42-d121a1d4f449" TYPE="ext4" 
/dev/sdd2: LABEL="Epsilon" UUID="df252263-b47c-403b-9c7a-d6bbb2224420" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdg1: LABEL="KTKAT 16GB" UUID="18CA-0CD8" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr1 on /cdrom type iso9660 (rw)
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
/dev/sdg1 on /media/KTKAT 16GB type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 2f3d7d5b-37f1-44ba-bdcf-a09ddaa253fb
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2f3d7d5b-37f1-44ba-bdcf-a09ddaa253fb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=2f3d7d5b-37f1-44ba-bdcf-a09ddaa253fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2f3d7d5b-37f1-44ba-bdcf-a09ddaa253fb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=2f3d7d5b-37f1-44ba-bdcf-a09ddaa253fb ro single 
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2f3d7d5b-37f1-44ba-bdcf-a09ddaa253fb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=3b78e1f7-5070-444c-8696-719a3e7f6cb1 /home           ext3    defaults        0       2
# /media/alpha was on /dev/sde1 during installation
UUID=21bcf72f-62bb-4569-8396-6e54f82f4734 /media/alpha    ext3    defaults        0       2
# /media/beta was on /dev/sdf2 during installation
UUID=de8ea70e-2687-440f-b719-774a8d6ffb85 /media/beta     ext3    defaults        0       2
# /media/delta was on /dev/sdc1 during installation
UUID=44debf5a-88c7-405b-a802-d2e7ff6fe595 /media/delta    ext3    defaults        0       2
# /media/epsilon was on /dev/sdd2 during installation
UUID=df252263-b47c-403b-9c7a-d6bbb2224420 /media/epsilon  ext3    defaults        0       2
# /media/gamma was on /dev/sdb1 during installation
UUID=8edb1624-f68b-4025-9634-7995c658c174 /media/gamma    ext3    defaults        0       2
# /tmp was on /dev/sdd1 during installation
UUID=29192e7b-6738-4fb9-9c42-d121a1d4f449 /tmp            ext4    defaults        0       2
# swap was on /dev/sdf1 during installation
UUID=189340b7-f668-4bd7-ace8-b59c7b859110 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |.c...3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 03 02  |.e.r....r;.,.}..|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  3c 9d 45 13 00 00 80 01  |...<.u..<.E.....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 5e 30 31 01 00 fe  |......?...^01...|
000001d0  ff ff 83 fe ff ff 9d 30  31 01 d6 06 07 1c 00 00  |.......01.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```


any and all help is very much appreciated.

---

### Post by jward3010 on 2009-11-15
I'm sorry to see you're having no luck getting help on this. I'm having the same problem, after an install of Karmic 9.10 and restart I got same Error 15. 

While I was installing I noticed that my drives we're appearing as *"/nvidia/mapper/xxxxxxxx"* rather than the usual "/dev/sdXX" so I assume this has something to do with it.

Did you notice this about your install. I have Karmic installed on another laptop and it works flawlessly, just on this home PC did it have to misbehave itself.

Everything worked nicely in Jaunty so this is a regression.

---

### Post by ed-koala on 2009-11-15
I had the same issue, here is why - [http://ubuntuforums.org/showthread.php?t=1325871]("http://ubuntuforums.org/showthread.php?t=1325871")

Hope it helps you too!

---

### Post by jward3010 on 2009-11-15
> **ed-koala said:**
> I had the same issue, here is why - [http://ubuntuforums.org/showthread.php?t=1325871]("http://ubuntuforums.org/showthread.php?t=1325871")

Hope it helps you too!
Thanks, I'll give it a blast.

It's a pity, I went and installed Jaunty instead, but knowing it's this simple I'll definitely give Karmic another try now.

It's a probable cause alright, the nVidia controller has RAID possibilities, switched off in the BIOS and it never was a problem in the past with Jaunty, Hardy etc. but obviously Karmic is noticing the RAID functionality behind the fact.

I'll post back soon the result.

JUST NOTICED: the standard liveCD has the "nodmraid" option too so I'll give that a go before I download a whole alternate disk, this might save people the trouble.

---

