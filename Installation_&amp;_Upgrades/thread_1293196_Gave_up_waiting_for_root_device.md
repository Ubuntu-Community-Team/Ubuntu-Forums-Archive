---
title: "Gave up waiting for root device"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by perfunction on 2009-10-16
I'm attempting to run a triple-boot with Kubuntu 9.1 on a Macbook Pro which was already dual-booting Snow Leopard and Windows 7. My first install worked fine, and I was even able to boot into it the next day at work. But when I got home from work GRUB wouldn't get past the "GRUB _" screen. I eventually gave up and reinstalled Kubuntu which fixed my problem. 

I started tweaking my second install with stuff like kcmtouchpad, nvidia drivers, broadcom wifi drivers, vidalia/tor/proxychains, firefox, and dicked around with the opengl desktop animations. 

However, after a day of work in Windows 7 I come back home to a Kubuntu install that fails to boot. It gives me the "gave up waiting for root device" error and says it will dump me to a shell but NEVER does. I waited probably 30 minutes once. I've been trying to fix it by googling for two days now but my installation doesn't seem to come anywhere near anything in the forum threads I'm finding. I tried IRC but I'm not even being acknowledged there.

[[IMG]http://img193.imageshack.us/img193/9374/img0037cf.jpg[/IMG]](http://img193.imageshack.us/i/img0037cf.jpg/)

Here are my results from the boot script: (sdb is a flash drive I just setup hoping it boots faster than this live-cd)
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6ff8bb3

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   444,850,719   444,441,080 HFS+
/dev/sda3     445,112,864   582,916,112   137,803,249 Linux (usually)
/dev/sda4     582,916,113   625,140,722    42,224,610 Linux (usually)

/dev/sda4 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1037 MB, 1037303808 bytes
32 heads, 62 sectors/track, 1021 cylinders, total 2025984 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000eb52b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     2,025,663     2,025,602   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="EFI" UUID="640B-0804" TYPE="vfat" 
/dev/sda2: UUID="17bff7e1-5094-373a-8de9-ec5e37e891fb" LABEL="MacintoshHD" TYPE="hfsplus" 
/dev/sda3: UUID="84B89DA4B89D9570" LABEL="BOOTCAMP" TYPE="ntfs" 
/dev/sda4: UUID="fa1ef365-a19c-4edf-aa8e-f5628880fd59" TYPE="ext4" 
/dev/sdb1: LABEL="" UUID="37B0-26D6" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /sys/kernel/debug type debugfs (rw)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/37B0-26D6 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=lower,dmask=0077,utf8=1)
/dev/sda4 on /mnt/sysvol type ext4 (rw)

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set fa1ef365-a19c-4edf-aa8e-f5628880fd59
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
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set fa1ef365-a19c-4edf-aa8e-f5628880fd59
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fa1ef365-a19c-4edf-aa8e-f5628880fd59 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set fa1ef365-a19c-4edf-aa8e-f5628880fd59
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fa1ef365-a19c-4edf-aa8e-f5628880fd59 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set fa1ef365-a19c-4edf-aa8e-f5628880fd59
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=fa1ef365-a19c-4edf-aa8e-f5628880fd59 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set fa1ef365-a19c-4edf-aa8e-f5628880fd59
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=fa1ef365-a19c-4edf-aa8e-f5628880fd59 ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
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
menuentry "Mac OS X (on /dev/sda2)" {
	insmod hfsplus
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e6604c38b8d74507
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid e6604c38b8d74507 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 84b89da4b89d9570
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=fa1ef365-a19c-4edf-aa8e-f5628880fd59 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 298.4GB: boot/grub/grub.cfg
 298.4GB: boot/initrd.img-2.6.31-11-generic
 298.4GB: boot/initrd.img-2.6.31-14-generic
 298.4GB: boot/initrd.img-2.6.31-14-generic.bak
 298.4GB: boot/vmlinuz-2.6.31-11-generic
 298.4GB: boot/vmlinuz-2.6.31-14-generic
 298.4GB: initrd.img
 298.4GB: initrd.img.old
 298.4GB: vmlinuz
 298.4GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.c....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 00 80 b9 13 2c 23  |....t..F.f....,#|
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
000001b0  cd 10 ac 3c 00 75 f4 c3  b3 8b ff a6 00 00 00 fe  |...<.u..........|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |..........'@....|
000001d0  ff ff af fe ff ff 28 40  06 00 f8 a1 7d 1a 80 fe  |......(@....}...|
000001e0  ff ff 07 fe ff ff 20 e2  87 1a f1 b5 36 08 80 fe  |...... .....6...|
000001f0  ff ff 83 fe ff ff 11 98  be 22 e2 4b 84 02 55 aa  |.........".K..U.|
00000200


=============================== StdErr Messages: ===============================

sed: can't read sda2/etc/issue: No such file or directory

``` 

Thanks in advance.

---

### Post by perfunction on 2009-10-17
I was finally able to figure it out on my own thanks to this page:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I followed the guide to recover grub2 using my live cd and while editing my defaults file I uncommented this line:
GRUB_DISABLE_LINUX_UUID=true

---

### Post by munooka on 2009-10-26
Thanks this worked like a treat. Wonder why it stopped working after yesterdays's updates?

---

### Post by petersphilo on 2010-08-21
Thank you very much for this info!!

I was in the same situation, sometimes it would boot, and sometimes it would stop with the same exact screen.

I have tried your hint of uncommenting the line:
GRUB_DISABLE_LINUX_UUID=true

in the file:
/etc/default/grub

EDIT:
i actually forgot to run 'update-grub' and ran into the same problem again.
So, i basically rebooted (about 8 times) until i got to the login screen, and immediately ran 'update-grub'.
The problem has not occurred since, yay!



**So, the short and sweet (in 4 steps) is:**

**1-** While logged into Lucid, in the Terminal application, type the following:
sudo gedit /etc/default/grub

**2-** Uncomment the line that reads:
GRUB_DISABLE_LINUX_UUID=true

**3-** Save

**4-** run the following command:
sudo update-grub

You're done!!



and it has worked without a problem ever since!

So, again, Thank You!!
Be Well!

---

