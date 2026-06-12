---
title: "Hard drive boot fail?"
date: 2011-08-03
forum: Hardware
---

### Post by joibjorn on 2011-08-03
Hi guys.
I got an annoying boot "error" every time I boot my Ubuntu 11-04.

The error message is : "unable to mount /dev/sda1, press s to skip, or m for manual recovery" or something like that. 

This message repeats itself for every disk/partition i got, and for the last partition that boots i get this message "The disk drive for /IdontRemeber is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery.

Here's the kicker, if i press M, i get nowhere. If i press S, i get to login screen and everything seems to work great. But this "error" message is really annoying and i would be very happy if someone could help me? I've been googleing and searching like a mother, but i cant find anything thats helpfull. 

PS: Here's the outcome of sudo fdisk -l:
```
root@ubuntu:/home/john# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      106609   856332288   83  Linux
/dev/sda2   *      106609      119785   105838592    7  HPFS/NTFS
/dev/sda3          119785      121602    14588929    5  Extended
/dev/sda5          119785      121602    14588928   82  Linux swap / Solaris

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a785e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       46825   376120320   83  Linux
/dev/sdb2           46826       48642    14588929    5  Extended
/dev/sdb5           46826       48642    14588928   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dfc39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488385536   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e1cc8df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdc5               2      121601   976751968+   7  HPFS/NTFS

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00850085

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sde2           16709       91201   598365022+   f  W95 Ext'd (LBA)
/dev/sde5           16709       48579   256003776    7  HPFS/NTFS
/dev/sde6           48580       91201   342361183+   7  HPFS/NTFS

```

---

### Post by Blasphemist on 2011-08-03
Wow do you have a lot more space than I do. Please download, run and post the results of the boot info script. This will help a lot but also please describe what you OSs have installed and on what disc/partition. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by joibjorn on 2011-08-03
Hehe, so much space and its not even enough:o 
I run Ubuntu 11.04 on my primary drive (sd1 i think, i havent learned the difference between sd1-sdwhatever) i dualboot windows 7 from the same harddrive using grub. And i apparently got win XP on sdc5. This is greek to me, i only have 9 beans :P 
Here is the results:
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sde5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sde6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sde6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,712,666,623 1,712,664,576  83 Linux
/dev/sda2    *  1,712,666,624 1,924,343,807   211,677,184   7 NTFS / exFAT / HPFS
/dev/sda3       1,924,345,854 1,953,523,711    29,177,858   5 Extended
/dev/sda5       1,924,345,856 1,953,523,711    29,177,856  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   752,242,687   752,240,640  83 Linux
/dev/sdb2         752,244,734   781,422,591    29,177,858   5 Extended
/dev/sdb5         752,244,736   781,422,591    29,177,856  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1              16,065 1,953,520,064 1,953,504,000   f W95 Extended (LBA)
/dev/sdc5              16,128 1,953,520,064 1,953,503,937   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   976,773,119   976,771,072  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS
/dev/sde2         268,414,020 1,465,144,064 1,196,730,045   f W95 Extended (LBA)
/dev/sde5         268,414,083   780,421,634   512,007,552   7 NTFS / exFAT / HPFS
/dev/sde6         780,421,698 1,465,144,064   684,722,367   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        f8200683-68d2-4fab-afac-76e4c1d8763e   ext4       
/dev/sda2        04606DE4606DDD44                       ntfs       
/dev/sda5        db45fc3a-100c-4e2b-8855-15d010893bc6   swap       
/dev/sdb1        5D8CACD81372B5DD                       ntfs       Bilda og anna viktig
/dev/sdb5        4d7de875-792c-4723-9ebd-c451e97c3aa0   swap       
/dev/sdc5        0658E80F58E7FB77                       ntfs       TERRA
/dev/sdd1        43938655-e856-464d-bfab-95a3b2656391   ext4       Shait
/dev/sde1        DC24AC8A24AC696A                       ntfs       
/dev/sde5        14A06FBCA06FA34A                       ntfs       Div
/dev/sde6        3A28747B28743849                       ntfs       Film åg musikk

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
set locale_dir=($root)/boot/grub/locale
set lang=nb_NO
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.38-10-generic-pae (gjennoprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, med Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.38-8-generic-pae (gjennoprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.35-28-generic-pae (gjennoprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 04606DE4606DDD44
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sde1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sde,msdos1)'
	search --no-floppy --fs-uuid --set=root DC24AC8A24AC696A
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f8200683-68d2-4fab-afac-76e4c1d8763e  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=db45fc3a-100c-4e2b-8855-15d010893bc6  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdd1                                  /media/sdd1     ntfs  defaults                  0  0  
/dev/sdd5                                  /media/sdd5     swap  defaults                  0  0  
/dev/sda2                                  /media/sda2     ntfs  defaults                  0  0  
/dev/sdb5                                  /media/sdb5     ntfs  defaults                  0  0  
/dev/sdc1                                  /media/sdc1     ext4  defaults                  0  0  
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 742.136756897 = 796.863275008  boot/grub/core.img                             1
 632.387714386 = 679.021137920  boot/grub/grub.cfg                             1
 761.930664062 = 818.116820992  boot/initrd.img-2.6.35-28-generic-pae          2
 644.630123138 = 692.166324224  boot/initrd.img-2.6.38-10-generic-pae          2
 590.821701050 = 634.389970944  boot/initrd.img-2.6.38-8-generic-pae           2
 746.042430878 = 801.056960512  boot/vmlinuz-2.6.35-28-generic-pae             1
 759.101993561 = 815.079559168  boot/vmlinuz-2.6.38-10-generic-pae             1
 589.540466309 = 633.014255616  boot/vmlinuz-2.6.38-8-generic-pae              1
 644.630123138 = 692.166324224  initrd.img                                     2
 590.821701050 = 634.389970944  initrd.img.old                                 2
 759.101993561 = 815.079559168  vmlinuz                                        1
 589.540466309 = 633.014255616  vmlinuz.old                                    1

================================ sde1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  74 84 63 41 70 93 4f 16  6d c0 c1 50 31 30 03 50  |t.cAp.O.m..P10.P|
00000010  44 36 22 d7 d9 6c 85 1d  10 b9 a9 aa d7 98 0c 00  |D6"..l..........|
00000020  eb 39 cc 3d 0d 95 fb 4e  58 c6 04 1a cd d5 f2 ef  |.9.=...NX.......|
00000030  55 bb 58 d0 0c 29 b8 3b  ce 79 6d 5e 94 f6 33 9a  |U.X..).;.ym^..3.|
00000040  e0 9e e5 c5 63 6e 09 d5  84 41 ba a3 30 8e 7b ae  |....cn...A..0.{.|
00000050  d4 8d 87 eb e3 5d ff 54  e3 b9 b2 28 9d a9 55 ae  |.....].T...(..U.|
00000060  4b d2 b9 b0 37 ae e1 dd  e4 0a c9 1d ec 4b 2b af  |K...7........K+.|
00000070  0d 59 c7 0a 29 22 9b 8e  5d 08 62 09 ea 31 b6 f9  |.Y..)"..].b..1..|
00000080  cb bb b5 36 52 c5 b9 be  29 fc c4 a5 82 8c 4a 21  |...6R...).....J!|
00000090  d9 5f 4e 47 6d 56 bd 87  3e e2 bd 85 1e 55 1a 51  |._NGmV..>....U.Q|
000000a0  9d 23 a5 d3 3a 45 0f 4f  b9 3c 51 2e e0 d5 89 f2  |.#..:E.O.<Q.....|
000000b0  bb aa 9b 7b 53 9e 6d df  ab 13 d0 2b b7 3e fd e7  |...{S.m....+.>..|
000000c0  ff f1 50 00 2e db c5 67  c6 94 7d 99 e8 c6 63 b2  |..P....g..}...c.|
000000d0  a8 38 ae 20 0e 18 2c 30  60 f4 31 92 83 c3 c0 71  |.8. ..,0`.1....q|
000000e0  22 99 84 c1 40 a0 60 70  0c 68 30 70 ec 81 1b 29  |"...@.`p.h0p...)|
000000f0  98 82 13 0c 2d 5c c9 da  c0 0c fc 65 01 e3 00 25  |....-\.....e...%|
00000100  c1 87 99 c9 00 a1 74 cc  f4 29 6b 27 d2 87 23 84  |......t..)k'..#.|
00000110  f2 29 b8 ab a9 39 5c a7  41 61 dc f5 2d 76 8b 29  |.)...9\.Aa..-v.)|
00000120  0d 37 f8 4f 2c 3c 8d af  02 00 55 8d 6b 38 6c d6  |.7.O,<....U.k8l.|
00000130  1c 8d 43 2f f3 60 d4 1e  ff fb e2 04 bb 8e e8 0c  |..C/.`..........|
00000140  69 50 1b 9b 7b 70 f8 8d  1a 23 73 6f 6e 1f 6d a3  |iP..{p...#son.m.|
00000150  40 6e 71 ed c4 09 34 68  4d cd bd b8 8d 8d 1d 20  |@nq...4hM...... |
00000160  6e 31 cc 7c 9d 2d 1b 54  24 56 4b a1 56 85 b1 1f  |n1.|.-.T$VK.V...|
00000170  eb 70 51 10 54 ae 49 76  39 16 75 16 e8 62 a9 89  |.pQ.T.Iv9.u..b..|
00000180  86 3e 9b 32 a6 50 30 b7  c1 bd 24 65 81 1d ec d3  |.>.2.P0...$e....|
00000190  be 8b 77 96 25 aa 63 dd  a6 72 60 44 20 a6 46 35  |..w.%.c..r`D .F5|
000001a0  e2 f9 8f 79 1f 43 c1 72  6f 99 74 c4 b9 7a 8c 4a  |...y.C.ro.t..z.J|
000001b0  a1 d8 6d 50 4f 56 18 b0  63 6d c6 2c 28 f2 00 fe  |..mPOV..cm.,(...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 bd 01 00 00  |...........8....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Blasphemist on 2011-08-03
As I go through this I'm going to make some notes.

Grub2 (2 variants of grub2) are installed on the mbr of sda and sdb, your first 2 drives. They each use the first partition on their respective drives for the rest of Grub2.

Windows is also installed twice on the mbr of sdc and sde, your 3rd and 5th drives. I don't think those drives have a boot flag set.

Your 4th drive, sdd has nothing in the mbr.

The first drive, sda has natty in sda1 (its first partition) and a bootable windows 7 in sda2 that was likely installed after ubuntu. In its extended partition is the swap partition.

It looks like sdb had windows installed first and then at least an attempt was made to install linux but that wasn't completed or it has been removed. 

For some reason sdc has an extended partition with xp in it apparently.

It seems sdd has only an extended partition and no logical partitions.

It seems sde had xp installed with abnormal partitioning. Most of the drive is extended partition with 2 logical windows partitions.

It looks like to me that maybe Fedora has been installed to sdc and sde at some point.

The root mount point for natty is sda1.

The Grub2 on sda has natty on sda1 and win 7 on sda2, xp on sde1. Nattys boot files look ok. The xp on sde1 has a boot.ini. An unknown boot loader is found on sdb2.

So how did all of this come about? Have these drives been cobbled together from other machines? Did you have a lot of install issues at some time? 

How do you really want to use all of these drives? What do you have that needs saved? Do you have critical data backed up and if so, where? I think you need some serious clean up of all of this but let me know about the answers to these questions and any additional background you can provide before I give any recommendations.

---

### Post by joibjorn on 2011-08-03
> So how did all of this come about? Have these drives been cobbled together from other machines? Did you have a lot of install issues at some time? 

How do you really want to use all of these drives? What do you have that needs saved? Do you have critical data backed up and if so, where? I think you need some serious clean up of all of this but let me know about the answers to these questions and any additional background you can provide before I give any recommendations. 
53 Minutes Ago 07:11 PM

yes, and no. I have bought new drives and upgraded my storage room over the years. I used sdb i think(the 400gig) as my pri drive(sd1)
But i have just now upgraded my OS drive to 1TB-drive. sd1 has the ubuntu install and the windows 7 install i want. All the other linux distros and win XP is not something i want on my computer.

I had ALOT of install issues over the years, and once upon a time i tried to clean it up and fix my drives, but it ended up with me managing to corrupt the ubuntu install as i was trying to backup it. I think i have reinstalled windows and ubuntu at least over 10 times this year alone, and every time i manage to fudge something up.

sde (my 5.disk i think) is actually my GF's disk.she had a motherboard issue on her comp, so we just plugged the drive into mine. I mount it in Ubuntu, so she can use it to access her crap.

I really need all this space, and i reallies that ALOT of space is gone to waste. I got alot of home made movies and pictures that are in RAW format and taking alot of space. furthermore i got tons of music and movies scattered on my drives because i have runned out of space. These are the things that are important to me, and i dont want to loose it. 

My most important drives are the /dev/sdb1 "bilda og anna viktig" and /dev/sdc1 "terra".

As you can see sdc1 is NTFS format, is there any way to format it with ext (4?) without loosing the data on it?

i got 500gig available on /dev/sdd1 (entire disk) but i cant mount it ```
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdd1 on /media/sdd1

```
Should i reformat it? and to what? I would like to use this disk as a storage for the MOST important backups. How can i mount it?

---

### Post by oldfred on 2011-08-03
I quickly found two things in fstab that are part of your problems. You cannot mount a swap as a regular partition but sdd5 does not exist anyway. And sdb5 is swap so you cannot mount it as NTFS. Delete both of these lines from fstab.

> /dev/sdd5   /media/sdd5     swap  defaults                  0  0  

/dev/[COLOR=Red]sdb5[/COLOR]  /media/sdb5[COLOR=Red]     ntfs[/COLOR]  defaults                  0  0 

/dev/sda1        f8200683-68d2-4fab-afac-76e4c1d8763e   ext4       
/dev/sda2        04606DE4606DDD44                       ntfs       
/dev/sda5        db45fc3a-100c-4e2b-8855-15d010893bc6   swap       
/dev/sdb1        5D8CACD81372B5DD                       ntfs       Bilda og anna viktig
/dev/[COLOR=Red]sdb5[/COLOR]        4d7de875-792c-4723-9ebd-c451e97c3aa0 [COLOR=Red]  swap[/COLOR]       
/dev/sdc5        0658E80F58E7FB77                       ntfs       TERRA
/dev/sdd1        43938655-e856-464d-bfab-95a3b2656391   ext4       Shait
/dev/sde1        DC24AC8A24AC696A                       ntfs       
/dev/sde5        14A06FBCA06FA34A                       ntfs       Div
/dev/sde6        3A28747B28743849                       ntfs       Film åg musikk
With multiple drives, I prefer to have each operating system on a separate drive as that helps avoid conflicts and if one drive fails you can still boot with the other. I also like to have Ubuntu on every drive except the windows one.

Some interesting points:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Other errors mounting or slow mounting may be helped by chkdsk in windows or e2fsck in Ubuntu for ext family of formats.

#From liveCD so everything is unmounted,swap off if necessary, change sdd1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdd1
#if errors:
sudo e2fsck -f -y -v /dev/sdd1

Some of your issues may be by mounting by device and with so many drives any change may change a device from sda to sdb etc.
Better to mount by UUID or by label.

---

### Post by Blasphemist on 2011-08-03
Ok, that all helps a lot. Let's start with sdd. It isn't mounting so you can run GParted from natty and get it ready. Then you can use it to put "stuff" on while you clean up other drives. I think it will help if you better understand the way to refer to drives and partitions correctly. The notation is sdXY. X is the drive letter sequence. The first drive is sda, second is sdb, etc. Y is the partition number on each drive. So sda1 is the first partition on the first disk. And sdb5 is the fifth partiton on the the second drive. Complicating this is that some numbers are skipped, sometimes. Each disc can have 4 primary partitions. They are always 1-4. If you create just one primary partition and within it one logical partition, you will have sdd1 and sdd5 for example on the 4th hard disc. An extended partition is a primary partition that can contain logical partitions. 

Delete the existing partition on sdd. Then create an extended partition that includes the whole drive. Within that extended partition, create a logical partition that fills the whole extended partition. Format the partition as NTFS and give it a label but no mount point. Using NTFS will ensure that you can access this from both windows and ubuntu. Use this instruction on mounting the partition in ubuntu. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ideally you'll be able to move enough from sdb, your second drive that is smaller than sdd, to sdd and then you can fix up sdb doing much the same thing again. But one thing at a time. If any of this stops Grub2 from booting something, boot to a live cd and come back here but if you are careful we'll make progress.

---

### Post by joibjorn on 2011-08-03
> Delete the existing partition on sdd. Then create an extended partition that includes the whole drive. Within that extended partition, create a logical partition that fills the whole extended partition. Format the partition as NTFS and give it a label but no mount point. Using NTFS will ensure that you can access this from both windows and ubuntu. Use this instruction on mounting the partition in ubuntu. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
This is now A-OK. it worked like a charm. Now moving and deleting stuff. my plan is now that i am gonna install windows 7 on sdb and keep/reinstall ubuntu on sda. Thanks for the help so far. I will keep you guys updated, as i am sure that i am gonna fudge something up during this process.

---

### Post by oldfred on 2011-08-03
With multiple drives & multiple systems I find I use the boot script a lot. It is just about the only way to see what is installed where and it documents some partition info that if you had to you could use to recover a partition manually. So keep boot script handy and learn enough to understand where grub is installed and what is where.

Generally windows works 'better' on sda. It may install its boot partition and MBR on sda even if you install in sdb. We have seen several users that lost the boot files that way, not knowing the 200MB system partition on sda belonged to windows.

---

### Post by joibjorn on 2011-08-05
Ok guys. have been working all day and night with deleting and moving stuff around on the drives. 
here's my fstab list now:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      106609   856332288   83  Linux
/dev/sda2   *      106609      119785   105838592    7  HPFS/NTFS
/dev/sda3          119785      121602    14588929    5  Extended
/dev/sda5          119785      121602    14588928   82  Linux swap / Solaris

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a785e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48642   390710272    5  Extended
/dev/sdb5               1       48642   390709248    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e1cc8df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976760832    5  Extended
/dev/sdc5               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dfc39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488385536    5  Extended
/dev/sdd5               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00850085

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91202   732572672    5  Extended
/dev/sde5               1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdf: 16.2 GB, 16240345088 bytes
64 heads, 32 sectors/track, 15488 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000de412

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       15488    15859696    7  HPFS/NTFS

```
is this improvement? I sure hope so. Now i get boot error only on sda and sdc and /storage.

here's the bootlog: 
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows Vista/7
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 32.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,712,666,623 1,712,664,576  83 Linux
/dev/sda2    *  1,712,666,624 1,924,343,807   211,677,184   7 NTFS / exFAT / HPFS
/dev/sda3       1,924,345,854 1,953,523,711    29,177,858   5 Extended
/dev/sda5       1,924,345,856 1,953,523,711    29,177,856  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   781,422,591   781,420,544   5 Extended
/dev/sdb5               4,096   781,422,591   781,418,496   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,523,711 1,953,521,664   5 Extended
/dev/sdc5               4,096 1,953,523,711 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   976,773,119   976,771,072   5 Extended
/dev/sdd5               4,096   976,773,119   976,769,024   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048 1,465,147,391 1,465,145,344   5 Extended
/dev/sde5               4,096 1,465,147,391 1,465,143,296   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 16.2 GB, 16240345088 bytes
64 heads, 32 sectors/track, 15488 cylinders, total 31719424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             32    31,719,423    31,719,392   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        f8200683-68d2-4fab-afac-76e4c1d8763e   ext4       
/dev/sda2        04606DE4606DDD44                       ntfs       
/dev/sda5        db45fc3a-100c-4e2b-8855-15d010893bc6   swap       
/dev/sdb5        0862851B13B03F06                       ntfs       Windows
/dev/sdc5        30C068025CEEF15A                       ntfs       Terra
/dev/sdd5        673CAEE5061DEB1C                       ntfs       TEmP
/dev/sde5        618A15EE4F493B62                       ntfs       Jeanett
/dev/sdf1        56CB-DB50                              vfat       Nytt volum

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5        /media/sdb5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde5        /home/john/jeanett       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdf1        /media/Nytt volum        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
set locale_dir=($root)/boot/grub/locale
set lang=nb_NO
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.38-10-generic-pae (gjennoprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, med Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.38-8-generic-pae (gjennoprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, med Linux 2.6.35-28-generic-pae (gjennoprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=f8200683-68d2-4fab-afac-76e4c1d8763e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f8200683-68d2-4fab-afac-76e4c1d8763e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 04606DE4606DDD44
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sde1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sde,msdos1)'
	search --no-floppy --fs-uuid --set=root DC24AC8A24AC696A
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f8200683-68d2-4fab-afac-76e4c1d8763e  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=db45fc3a-100c-4e2b-8855-15d010893bc6  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdd1                                  /media/sdd1     ntfs  defaults                  0  0  
/dev/sdd5                                  /media/sdd5     swap  defaults                  0  0  
/dev/sda2                                  /media/sda2     ntfs  defaults                  0  0  
/dev/sdb5                                  /media/sdb5     ntfs  defaults                  0  0  
/dev/sdc1                                  /media/sdc1     ext4  defaults                  0  0  
UUID=673CAEE5061DEB1C /storage ntfs defaults 0 0
UUID=618A15EE4F493B62 /home/john/jeanett ntfs defaults 0 0
UUID=0862851B13B03F06 /storage ntfs defaults 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 742.136756897 = 796.863275008  boot/grub/core.img                             1
 632.387714386 = 679.021137920  boot/grub/grub.cfg                             1
 761.930664062 = 818.116820992  boot/initrd.img-2.6.35-28-generic-pae          2
 644.630123138 = 692.166324224  boot/initrd.img-2.6.38-10-generic-pae          2
 590.821701050 = 634.389970944  boot/initrd.img-2.6.38-8-generic-pae           2
 746.042430878 = 801.056960512  boot/vmlinuz-2.6.35-28-generic-pae             1
 759.101993561 = 815.079559168  boot/vmlinuz-2.6.38-10-generic-pae             1
 589.540466309 = 633.014255616  boot/vmlinuz-2.6.38-8-generic-pae              1
 644.630123138 = 692.166324224  initrd.img                                     2
 590.821701050 = 634.389970944  initrd.img.old                                 2
 759.101993561 = 815.079559168  vmlinuz                                        1
 589.540466309 = 633.014255616  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```
So, what now? I want to remove/move win 7 on sdb and reinstall ubuntu on sda. would a reinstall remove my errors and write in the drives in fstab on installation? or do i have to manually write them in fstab after install?

---

### Post by oldfred on 2011-08-05
You will have to add entries to fstab after you install. The new versions do allow some extra mounts but I have tried mounting NTFS as the installer does not normally include that driver since Ubuntu cannot boot from NTFS.

Your newer fstab has two entries with /storage. Probably only the second one will appear to be mounted and you are wondering what happened to the first.

Is there some reason why you only have sda5 partitions with no primary partitions on several of your drives. I prefer to use 1 or 2 primary partitions, then the extended and keep one primary for future use. And I then have most of my space in the extended so I can create many logical partitions.

If you have made a lot of changes to your Ubuntu install and are doing a clean install, backup your /home. since most of your data is going into other shared partitions, do really do not need a separate /home partition. But your Ubuntu partition for the system when you have little or no data in your /home only needs to be 20 or 25GB. System is slightly more efficient if all files are near each other on a large drive.

---

### Post by joibjorn on 2011-08-08
> Is there some reason why you only have sda5 partitions with no primary partitions on several of your drives. I prefer to use 1 or 2 primary partitions, then the extended and keep one primary for future use. And I then have most of my space in the extended so I can create many logical partitions.
I did it because Blasphemist told me to. > Delete the existing partition on sdd. Then create an extended partition that includes the whole drive. Within that extended partition, create a logical partition that fills the whole extended partition. Format the partition as NTFS and give it a label but no mount point. Using NTFS will ensure that you can access this from both windows and ubuntu. Use this instruction on mounting the partition in ubuntu. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
Was this wrong? how should i format the drives? I thought ext 4 was the linux "partition", not ntfs.

---

### Post by oldfred on 2011-08-08
NTFS is a windows format that Ubuntu reads & writes just fine. So it is good for sharing data between windows & Ubuntu. It is usually best not to directly read/write into a system partition or windows c: drive as from Ubuntu you can see and possibly accidentally move or damage all system files. If you want you can mount the c: drive as read only so you can get data from it without worrying about possible problems.

It is just a bit unusual to have one large extended partition with only a logical, but that will work. If you ever want additional partitions you can then shrink the NTFS inside the extended and create new logicals at the end.

---

### Post by Blasphemist on 2011-08-08
> **joibjorn said:**
> I did it because Blasphemist told me to. 
Was this wrong? how should i format the drives? I thought ext 4 was the linux "partition", not ntfs.

OK, timeout. You did what I asked on sdd and it accomplished exactly what was desired. You had files to cleanup or "backup" and you were able to do exactly that. You have that drive partitioned for maximum space and formatted as ntfs so that it can be used by both windows and ubuntu. If you have moved or copied all the files you need from sda and sdb, you could remove that drive and set it aside for now if you want.

You seem to have a plan for installing ubuntu on sda and I think I understand you desire windows on sdb. Is that right? If so that seems appropriate to me and follows oldfred's recommendation of putting an OS on each drive. That is one drive that is 1TB (sda) and one that is 400GB (sdb). Between sdc, sdd and sde you have another 2.25TB a huge amount of storage.

If you have all files desired salvaged from sdc and sde, you could plan for using them as backup's for sda and sdb respectively. When everything is all set up you could then move the files from your current sdd to any location you desire. I think you could also set up a software raid but that adds complexity.

I think you might want to consider having windows on sda and ubuntu on sdb with windows installed first because the windows install is more microsoft standard then but that isn't required. You should try to think about what your long term needs are. Do you ever expect to install other distros for example? Do you have a plan for using this much storage? You have a huge amount of storage. If you never use near all of it fine but if you have a plan for storing a huge amount of data, that will affect what you build from here. There are a few hard and fast rules for partitioning your drives but limitations come into play more for those of us with only hundreds of MB of space than for you with TB's worth.

My recommendation would be to plan out what you desire and ask for guidance on how to get there. I know that is what you have been trying to do and how we have been trying to help but I'm not sure we are all on the same page right now. If you removed sdd right now and set it aside, would everything of importance be safe? If you had to re-install OS's and applications, do you have what you need? You had a bit of a confused mess from putting all of this together but I think you are getting to where you desire. What do you think?

---

### Post by joibjorn on 2011-08-08
> You seem to have a plan for installing ubuntu on sda and I think I understand you desire windows on sdb. Is that right? If so that seems appropriate to me and follows oldfred's recommendation of putting an OS on each drive. That is one drive that is 1TB (sda) and one that is 400GB (sdb). Between sdc, sdd and sde you have another 2.25TB a huge amount of storage.
Thats correct. I want ubuntu on sda and windows on sdb. 
I want to reformat the sda drive completely and do a clean install of ubuntu. If i do that, the ubuntu install will format the sda drive for me? with swap and everything, right?

> Do you ever expect to install other distros for example? Do you have a plan for using this much storage? You have a huge amount of storage. If you never use near all of it fine but if you have a plan for storing a huge amount of data, that will affect what you build from here. There are a few hard and fast rules for partitioning your drives but limitations come into play more for those of us with only hundreds of MB of space than for you with TB's worth.
As i said, sda for ubuntu, sdb for windows, sdc for MY storage needs, sde for my girlfriends storage needs, and sdd for future projects? maybe a other distro? have no idea yet. could be nice with 500gig's unallocated space sitting there and waiting for some good use.

>  If you removed sdd right now and set it aside, would everything of importance be safe? If you had to re-install OS's and applications, do you have what you need? You had a bit of a confused mess from putting all of this together but I think you are getting to where you desire. What do you think? Everything important is safe, and A-OK. I think i have a much better understanding over what i self want. sdb (windows disk) is the only one that needs to be in NTFS, because i can store my music and my pictures there so that i can access it in both win and ubuntu. The win OS will be used ONLY for battlefield 2, Itunes and photoshop. I have NO need what so ever to access the other drives via win7, because its a shitty OS and i dont like it. But i digress..
So to recap:
SDA- want clean install of disk with UBUNTU.
SDB- want clean install of disk with WIN 7.
SDC- My storage needs, EXT4 (only accessible from UBUNTU)
SDD- Backup disk/unallocated space/test drive for other distros/ dont really care.
SDE- My girlfriends storage needs, EXT4 (only accessible from UBUNTU)

By the way, thanks a MILLION for the help so far, you guys are doing a GREAT job:KS:)

---

### Post by oldfred on 2011-08-08
See my post #9, I still think windows in sda is better. You can move connections in SATA ports if you want to change which drive is sda. Windows will try to put its boot files in sda if you install to sdb.

---

### Post by joibjorn on 2011-08-08
Allright. That makes sence, but will windows or ubuntu be listed on top in grub2 if i do the switcharoo on the drives and install win on sda? I want to be able to turn on my comp and walk away for a few minutes and when i come back, ubuntu is logged in and ready for use.( this is how it is today)

---

### Post by oldfred on 2011-08-08
Grub's os-prober always finds other systems last unless you modify grub manually or with one of the newer gui tools to modify grub's settings.

---

### Post by Blasphemist on 2011-08-08
Good, so windows will be only on sda and that will be the only ntfs drive. You'll be able to install windows that way easily. You could boot to the ubuntu live cd before you do that and remove the existing partitions from sda but I don't think you'd have to do that. I believe windows will install to that drive and use the whole sda if that is what you tell it to do. Still if you delete the partitions on that drive and let windows create it's own that will work too.

I'd recommend that you create the partitions on sdb ahead of the install of ubunutu but I believe it will also do as you ask and use all of sdb if that is what it's told. That would include it creating a swap partition. But I would partition it ahead of time. When told to use the whole drive I don't really know what it will do for sure but I expect it will create sda1 as an primary extended partition using the whole drive and within that extended partition create sda5 for data and sda6 as swap at the end of the drive. That is also what I'd do manually though I might only use 50GB or so for / mount point and the rest of the data part of the drive for /Home. And if you do this manually remember that swap should be a bit larger than the most memory you expect to ever use.

Sdc and sde also only need a primary extended partition with a logical partition within. For each of these drives the extended partition would be the whole drive and the logical partition within would be all of the space within the extended partition. For sure you could partition these differently but there isn't any need in anything more complicated that I can see.

You could do all of this partitioning ahead of time while booted to the live ubuntu cd, and when ready start the installs. When finished you'd move the data from sdd to it's desired location. When everything is moved from sdd, you could then again create one large extended partition. Then within it create a bunch of logical 50-75 GB partitions for distros or whatever.

As oldfred said, when you have only 2 OS's, grub2 is real simple. It will always have the linux distro first and then windows. And grub2 can easily be told which OS to boot by default if no action is taken. When you go beyond 2 OSs, multiple linux distros, it is best to configure the built in custom grub script and disable some of the default grub scripts to manipulate exactly what shows up in grub2 and in what order. But that is more than you need to worry about now and its not real complex.

Good luck, you're about there!

---

### Post by joibjorn on 2011-08-09
> SDA- want clean install of disk with UBUNTU.
SDB- want clean install of disk with WIN 7.
SDC- My storage needs, EXT4 (only accessible from UBUNTU)
SDD- Backup disk/unallocated space/test drive for other distros/ dont really care.
SDE- My girlfriends storage needs, EXT4 (only accessible from UBUNTU)

Ok. so far, so good.
SDA- got a clean install of disk with WIN 7.
SDB- accidentally connected wrong drive here, so this is now MY storage needs(EXT4) .
SDC- Fresh install of Ubuntu WITHOUT boot errors... yey..!
SDD- Backup disk/unallocated space/test drive for other distros/ dont really care.
SDE- My girlfriends storage needs, EXT4 (only accessible from UBUNTU)

Is there any problem with ubunut is on SDC, not SDB? if so, can i just swap SATA-connectors inside the comp without confusing grub?

Right now i am working on moving my stuff around and reformatting them to EXT4, not NTFS. Fixing my mistake from earlier. but SDA and SDB is complete and just the way i want them... i think. take a look at my fdisk-l:
```
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a785e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       48642   390606848    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e1cc8df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832    5  Extended
/dev/sdb5               2      121601   976752000   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121080   972567552   83  Linux
/dev/sdc2          121080      121602     4192257    5  Extended
/dev/sdc5          121080      121602     4192256   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dfc39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488385536    5  Extended
/dev/sdd5               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00850085

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91202   732572672    5  Extended
/dev/sde5               1       91202   732571648    7  HPFS/NTFS

```
As mentioned above, sdd and sde is going to be converted to EXT4.

But, when i was about to check out fstab.list it was empty? what the heck? i had it before reinstalling everything. how can i salvage this? By the way, the guide you provided: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) was a nice guide, but what if i want to auto mount the drives in /media or better, they show up in *places-computer *done mounted on boot? and is it possible to remove the icons on the desktop?

---

### Post by oldfred on 2011-08-09
If it is working I would not change it. 

Ubuntu normally works from UUIDs so changing drive order does not change anything, but if your fstab uses device like /dev/sdc then it will have problems. Same with grub2. It uses a hard disk like hd2 or /dev/sdc but then does a search on UUID if the drive is not found.

I create mount points in /mnt instead of /media or /home. It depends on whether you want to easily see them in Nautilus or /home. When in /mnt you have to search  to find them. But i use links to put folders into my /home from /mnt/data or /mnt/shared partitions.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by joibjorn on 2011-08-10
>  create mount points in /mnt instead of /media or /home. It depends on  whether you want to easily see them in Nautilus or /home. When in /mnt  you have to search  to find them. But i use links to put folders into my  /home from /mnt/data or /mnt/shared partitions.

have been reading the links and got a much better understanding now. But one question though: If i edit my fstab.list and create mount points in /whatever or /media or /mnt and put all my drives except SDA and SDB in there, can i then access them through GUI and "click" on their respective icons? or will every drive get mashed up in that same folder? maybe i should mount one drive in /driveA and one in /driveB and so on? What do you mean by "search to find them" and using links to put folders in the drives? 
Side note:
> /mnt-mount-Temporary mounting points
is that correct? /mnt is temp?

---

### Post by oldfred on 2011-08-10
If not in /home your have to use Nautilus to to to system and drill down thru /mnt to the mount point in /mnt. Also since that is off / (root) it will default to root ownership & permissions so you have to reset those. If you directly mount in /home it is easy to get to but can be too easy and show up twice in Nautilus. 

However you mount other partitions you have to have an unique mount for each so they do not get 'mashed up'. I try to use labels so all partitions not mounted get mounted by the label. And I try to use mount points that explain what it is and driveA, driveB is fine if it works for you. I use /mnt/data for my ext3 partition and /mnt/shared for my NTFS partition as that was originally for sharing with XP. But I link folders like Documents, Music etc into my /home from my /mnt/data so my system sees the normal folders but the data is really in my data partition. My /home then only has the hidden user settings and very little user data.

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by joibjorn on 2011-08-17
OK. thanks alot guys. I'm gonna mark this as solved, since i now got rid of the errors during boot and i now got a fresh install of everything.

---

