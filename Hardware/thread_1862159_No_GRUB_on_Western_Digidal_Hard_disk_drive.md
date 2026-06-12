---
title: "No GRUB on Western Digidal Hard disk drive"
date: 2011-10-16
forum: Hardware
---

### Post by Klaten on 2011-10-16
Hi, All!
I have a problem with my WD2500BEVS-22USTO HDD. I bought new HDD to my laptop becouse my old disk have not enaugh space to hold 2 operating systems. I need windows for some programs and i just need more ubuntu. So i make few partiotions on this disk and install windows 7 (starting with no promblems) then i install ubuntu 11.10 and reboot my PC. Then i saw insteed of GRUB something like this:

```
error: no such partition
grub rescue>
```

then i tried reinstall GRUB from liveCD with chroot but that's doasn't work. Only bootrec /fixmbr help from windows cd but i can't start ubuntu. Then i tried install ubuntu on my old FUJITSU 80GB disk and on this i have no problems. So why GRUB doasn't work on WD disk? maybe u have some idea what to do...

boot_info_sript:
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    61,442,047    61,235,200   7 NTFS / exFAT / HPFS
/dev/sda3          61,442,048   307,202,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda4         307,204,094   488,396,799   181,192,706   5 Extended
/dev/sda5         307,204,096   311,107,583     3,903,488  82 Linux swap / Solaris
/dev/sda6         311,109,632   359,935,999    48,826,368  83 Linux
/dev/sda7         359,938,048   488,396,799   128,458,752  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7438B9EE38B9AF8A                       ntfs       Zastrze&#380;one przez system
/dev/sda2        C280E96A80E9657F                       ntfs       
/dev/sda3        B416B76F16B7316A                       ntfs       
/dev/sda5        1c12f254-477a-4b1f-8ba0-e6435e84509d   swap       
/dev/sda6        2ce50258-082c-4fe1-9919-949bf68a9f27   ext4       
/dev/sda7        8f52d21c-ca31-4029-a065-8946522be48f   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 2ce50258-082c-4fe1-9919-949bf68a9f27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 2ce50258-082c-4fe1-9919-949bf68a9f27
  set locale_dir=($root)/boot/grub/locale
  set lang=pl_PL
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
   recordfail
   set gfxpayload=$linux_gfx_mode
   insmod gzio
   insmod part_msdos
   insmod ext2
   set root='(hd0,msdos6)'
   search --no-floppy --fs-uuid --set=root 2ce50258-082c-4fe1-9919-949bf68a9f27
   linux   /boot/vmlinuz-3.0.0-12-generic root=UUID=2ce50258-082c-4fe1-9919-949bf68a9f27 ro   quiet splash vt.handoff=7
   initrd   /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
   recordfail
   insmod gzio
   insmod part_msdos
   insmod ext2
   set root='(hd0,msdos6)'
   search --no-floppy --fs-uuid --set=root 2ce50258-082c-4fe1-9919-949bf68a9f27
   echo   'Loading Linux 3.0.0-12-generic ...'
   linux   /boot/vmlinuz-3.0.0-12-generic root=UUID=2ce50258-082c-4fe1-9919-949bf68a9f27 ro recovery nomodeset 
   echo   'Loading initial ramdisk ...'
   initrd   /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
   insmod part_msdos
   insmod ext2
   set root='(hd0,msdos6)'
   search --no-floppy --fs-uuid --set=root 2ce50258-082c-4fe1-9919-949bf68a9f27
   linux16   /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
   insmod part_msdos
   insmod ext2
   set root='(hd0,msdos6)'
   search --no-floppy --fs-uuid --set=root 2ce50258-082c-4fe1-9919-949bf68a9f27
   linux16   /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
   insmod part_msdos
   insmod ntfs
   set root='(hd0,msdos1)'
   search --no-floppy --fs-uuid --set=root 7438B9EE38B9AF8A
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=2ce50258-082c-4fe1-9919-949bf68a9f27 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=8f52d21c-ca31-4029-a065-8946522be48f /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1c12f254-477a-4b1f-8ba0-e6435e84509d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               4
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     4
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  df 75 94 93 68 87 8c 61  ad c5 ff 00 ff ff 00 ff  |.u..h..a........|
00000010  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000020  00 ff ff 00 ff ff 00 ff  b1 d4 e1 a8 d9 e5 a9 d1  |................|
00000030  e7 c3 ed f0 cd f6 f6 ce  f6 f7 cc f3 f6 ca f2 f5  |................|
00000040  c8 f2 f5 c9 f2 f5 c8 f1  f2 c7 ee f1 c2 ec ee b1  |................|
00000050  ed f1 bb b8 b9 af a9 aa  8a 88 89 68 68 68 ab ab  |...........hhh..|
00000060  ab 94 94 94 70 71 72 67  69 6b 6d 6e 70 83 83 83  |....pqrgikmnp...|
00000070  ff 00 ff ff 00 ff ff 00  ff ff 00 ff ff 00 ff ff  |................|
00000080  00 ff ff 00 ff ff 00 ff  9d e1 ea ae f5 f6 b6 f3  |................|
00000090  f6 c3 f2 f3 c9 f3 f3 c8  f2 f5 c8 f1 f3 c9 f3 f5  |................|
000000a0  c9 f2 f5 c9 f2 f5 c9 f1  f3 c8 f0 f2 bd f1 f3 aa  |................|
000000b0  eb f0 9d e2 e7 c3 be c0  a9 a6 a6 76 77 7a 66 68  |...........vwzfh|
000000c0  6a ac a9 a7 d5 d4 d3 ea  e3 de e4 dd d6 c4 bf bb  |j...............|
000000d0  8c 8a 88 77 79 7b ff 00  ff ff 00 ff ff 00 ff ff  |...wy{..........|
000000e0  00 ff ff 00 ff ff 00 ff  9d da e8 a9 ee f2 aa ee  |................|
000000f0  f3 b5 f0 f3 c1 f1 f3 c7  f1 f3 ca f3 f6 cc f3 f7  |................|
00000100  ca f3 f6 c8 f2 f3 be eb  ee aa e0 e4 94 d8 da 8c  |................|
00000110  d3 d6 8f d5 db 99 e0 e5  6c 6d 71 bb b8 b6 ab c7  |........lmq.....|
00000120  c2 9c ce cf 94 d5 db 84  c3 c8 80 b4 b7 98 b9 b5  |................|
00000130  b7 c7 bc cb c1 b8 71 74  76 ff 00 ff ff 00 ff ff  |......qtv.......|
00000140  00 ff ff 00 ff ff 00 ff  9d d9 e7 a9 f0 f2 a9 ee  |................|
00000150  f3 ac f2 f7 b5 f6 f8 bb  f2 f6 b7 ec ee b4 e6 ea  |................|
00000160  a8 de e1 99 d5 d9 91 d2  d6 93 d8 db 9d e4 e7 a6  |................|
00000170  ed f2 aa f0 f6 8b 8a 89  9b 98 95 ce ec e2 ac e3  |................|
00000180  e0 85 c1 c1 82 be bd 9e  d4 d1 ad df de 8d 99 92  |................|
00000190  8e 9c 91 b8 d1 c3 d2 c3  b6 79 7b 7c ff 00 ff ff  |.........y{|....|
000001a0  00 ff ff 00 ff ff 00 ff  a0 da e7 ab f0 f3 a8 ed  |................|
000001b0  f2 9f e6 ea 97 df e4 92  d8 dd 8b d0 d3 84 00 ef  |................|
000001c0  ff ff 82 ef ff ff 02 00  00 00 00 90 3b 00 00 ef  |............;...|
000001d0  ff ff 05 ef ff ff 02 96  3b 00 00 0a e9 02 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

P.S. Sorry for my english if i mixed something :)

---

