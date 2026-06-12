---
title: "Gparted problem, urgent, help needed ASAP"
date: 2011-08-20
forum: Hardware
---

### Post by Robboti on 2011-08-20
Hello again!

I was viewing how much space I have left on my WinXP and noticed that my total space had reduced from 160 Gb to ~149 Gb. I know this has something to do with my failed attempt to install WinXP/Ubuntu dual boot on same hard drive earlier this year (I use External Hard Drive for Ubuntu now.
So I started up Gparted on Ubuntu (Since I have failed to find similar software to Windows) and noticed that there were partition size of ~10 Gb on my int. Hard drive (Probably used to store files from that failed install). So I removed all empty space (~1,5 Gb) from it and moved it to my WinXP partition.
When I rebooted to windows it didn't start up (computer powers up and checks if I have Ubuntu-drive attached and goes to grub if I do). I therefore have few questions.

1) **Is it only taking really, really long time to start up, or will it start up at all?**
2) **Since I suspect it is the latter one, is there any ways to fix it?** I've heard one way that has something to do with WinXP recovery disc.
3) Since I don't have XP recovery disc nor even a DVD-Drive on my Acer eMachines 250 (altough I have External DVD-drive and my father owns a copy of recovery disc, but they didn't boot up), I'd like to know, **is there any ways to do it through Ubuntu?**

I would really, really appreciate help ASAP

Or at least tell me, how can I reinstall Windows in this situation. Like is there a way I could use Winnt32.exe in i386 folder? I tried it with Wine, but it doesn't work.

EDIT: I think it's irrelevant, but the 10 Gb partition I was talking about is named PQSERVICES. Perhaps it helps, perhaps it don't.

---

### Post by tom4everitt on 2011-08-20
Probably you changing partitions confused the Windows boot loader.

1. I don't think waiting will help.

2 and 3.

Can you boot Windows from Grub? Does Windows show up in your Grub list?

Otherwise you probably need to restore the Windows boot loader. There are lots of guides on how to this if you google, but I'm afraid most of them require a recovery disc. 

Two of them, randomly picked
[http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/](http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/)
[http://kb.acronis.com/content/1507](http://kb.acronis.com/content/1507)

Your best chance is probably to boot from that external cd drive of yours. Usually you're supposed to press F12 or Delete or something like that when the computer boots to get a boot menu (but that you surely know already).

---

### Post by Robboti on 2011-08-20
Windows shows up on grub, but I'm not able to boot to it. I've tried to press almost every possible button on startup (Not quite sure if all), but Can't get into boot menu and I'm too tired to keep trying. Perhaps tomorrow.
Thank you anyway.

---

### Post by oldfred on 2011-08-20
Lets wee what this shows.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
New Version 060 has improved formating and requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

---

### Post by Robboti on 2011-08-21
Ok. Here goes.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Lilo is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdc2 starts 
                       at sector 20981760. But according to the info from 
                       fdisk, sdc2 starts at sector 17313792. According to 
                       the info in the boot sector, sdc2 has 291596287 
                       sectors, but according to the info from fdisk, it has 
                       295264255 sectors.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Levy /dev/sda: 3998 Mt, 3998220288 tavua
49 päätä, 49 sektoria/ura, 3252 sylinteriä, yhteensä 7809024 sektoria
Yksiköt = 1 * 512 = 512 -tavuiset sektorit
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               8,064     7,809,023     7,800,960   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Levy /dev/sdb: 250.1 Gt, 250059349504 tavua
255 päätä, 63 sektoria/ura, 30401 sylinteriä, yhteensä 488397167 sektoria
Yksiköt = 1 * 512 = 512 -tavuiset sektorit
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   482,256,895   482,254,848  83 Linux
/dev/sdb2         482,258,942   488,396,799     6,137,858   5 Extended
/dev/sdb5         482,258,944   488,396,799     6,137,856  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Levy /dev/sdc: 160.0 Gt, 160041885696 tavua
255 päätä, 63 sektoria/ura, 19457 sylinteriä, yhteensä 312581808 sektoria
Yksiköt = 1 * 512 = 512 -tavuiset sektorit
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    17,313,791    17,313,729   2 XENIX root
/dev/sdc2    *     17,313,792   312,578,047   295,264,256   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C66E-9E04                              vfat       PUBLIC
/dev/sdb1        33c2bb95-577b-4840-8dae-c7fdf3fd64c3   ext4       
/dev/sdb5        aa62be9d-1032-49ec-a7b7-de945fc8579f   swap       
/dev/sdc1        01CC5CE0B1510B50                       ntfs       PQSERVICE
/dev/sdc2        F84674534674149A                       ntfs       OS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/PUBLIC            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sdc2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
set locale_dir=($root)/boot/grub/locale
set lang=fi_FI
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
menuentry 'Ubuntu, Linux-ydin 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=33c2bb95-577b-4840-8dae-c7fdf3fd64c3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, Linux-ydin 2.6.38-11-generic (toipumistila)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=33c2bb95-577b-4840-8dae-c7fdf3fd64c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, Linux-ydin 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=33c2bb95-577b-4840-8dae-c7fdf3fd64c3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, Linux-ydin 2.6.38-10-generic (toipumistila)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=33c2bb95-577b-4840-8dae-c7fdf3fd64c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, Linux-ydin 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=33c2bb95-577b-4840-8dae-c7fdf3fd64c3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, Linux-ydin 2.6.38-8-generic (toipumistila)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=33c2bb95-577b-4840-8dae-c7fdf3fd64c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 33c2bb95-577b-4840-8dae-c7fdf3fd64c3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01CC5CE0B1510B50
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root F84674534674149A
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdd1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=aa62be9d-1032-49ec-a7b7-de945fc8579f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 116.128688812 = 124.692230144  boot/grub/core.img                             1
 154.602794647 = 166.003486720  boot/grub/grub.cfg                             1
   0.437698364 = 0.469975040    boot/initrd.img-2.6.38-10-generic              3
   0.437698364 = 0.469975040    boot/initrd.img-2.6.38-10-generic.dpkg-bak     3
 116.132827759 = 124.696674304  boot/initrd.img-2.6.38-10-generic.new          1
   1.281742096 = 1.376260096    boot/initrd.img-2.6.38-11-generic              2
   6.817642212 = 7.320387584    boot/initrd.img-2.6.38-8-generic               2
   6.618473053 = 7.106531328    boot/vmlinuz-2.6.38-10-generic                 1
  17.298160553 = 18.573758464   boot/vmlinuz-2.6.38-11-generic                 2
   4.348937988 = 4.669636608    boot/vmlinuz-2.6.38-8-generic                  1
   1.281742096 = 1.376260096    initrd.img                                     2
   0.437698364 = 0.469975040    initrd.img.old                                 3
  17.298160553 = 18.573758464   vmlinuz                                        2
   6.618473053 = 7.106531328    vmlinuz.old                                    1

================================ sdc2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  f2 ed ee d3 8b 41 74 c8  b0 13 a3 5d fb 92 38 c6  |.....At....]..8.|
00000010  85 24 57 ee 8c a4 a8 20  e3 7e 65 bf a3 fa 5e f9  |.$W.... .~e...^.|
00000020  a8 4e 18 69 22 e8 d7 d0  27 90 ac c8 4b 99 8c 6e  |.N.i"...'...K..n|
00000030  20 16 51 10 d7 00 dc e9  c0 78 1e c2 ed e0 25 af  | .Q......x....%.|
00000040  ae 23 28 b2 2b d2 a3 78  f6 5c 64 fc 94 3a 90 4a  |.#(.+..x.\d..:.J|
00000050  15 28 c2 16 a4 4b 0c 84  07 6a 1b c3 41 12 32 cc  |.(...K...j..A.2.|
00000060  1f cd 41 0e c5 5a 00 1c  37 d1 ea 5d f7 d0 6c bd  |..A..Z..7..]..l.|
00000070  8e bd cb 60 14 ea 5c 4a  cf b7 78 17 bd e6 a0 aa  |...`..\J..x.....|
00000080  1f a8 81 d7 11 e3 06 1d  11 4f 64 41 95 bf 3a 25  |.........OdA..:%|
00000090  a1 3b 8b 47 44 34 e2 9e  3f c1 53 26 84 c4 95 b1  |.;.GD4..?.S&....|
000000a0  d0 19 0c 76 2f c7 d8 d9  a1 3a eb 12 8d 64 1c de  |...v/....:...d..|
000000b0  70 f6 23 30 59 8e c6 dd  74 e6 cf 50 b6 0c 2c 3c  |p.#0Y...t..P..,<|
000000c0  49 7d fc 42 41 6d 94 b3  04 f2 a1 2b ff 22 2d 4f  |I}.BAm.....+."-O|
000000d0  1e 55 b5 7a 6a 59 23 6a  91 88 0a f3 70 15 87 ac  |.U.zjY#j....p...|
000000e0  b3 31 74 a3 5f 32 5e 0e  5c d3 a8 f0 08 57 98 d6  |.1t._2^.\....W..|
000000f0  cc bc 5a 85 a3 f1 1e a5  af 05 23 6f d4 48 c6 61  |..Z.......#o.H.a|
00000100  2c 9a 92 f5 b4 79 4f 44  ce 3f 20 bc d0 60 73 d4  |,....yOD.? ..`s.|
00000110  97 7f 3b b4 18 b8 d5 ec  f7 b8 41 23 01 05 08 b9  |..;.......A#....|
00000120  d0 18 78 94 58 9d 91 b3  73 99 28 f2 6e a2 e4 a3  |..x.X...s.(.n...|
00000130  9f 0c 72 64 f4 0f 67 a2  84 0a 79 72 16 a9 6e 1b  |..rd..g...yr..n.|
00000140  c4 08 49 ea 6f 01 3f c3  6d 3c dc f0 04 7d 09 aa  |..I.o.?.m<...}..|
00000150  02 b8 20 f3 4f 55 f6 27  75 58 f1 b6 38 92 18 e2  |.. .OU.'uX..8...|
00000160  23 cc 1e 4c 18 03 76 d3  de 8d 61 17 b7 4f 03 46  |#..L..v...a..O.F|
00000170  e7 e8 66 c5 4d ea a1 d4  ee 01 cd 57 84 20 26 68  |..f.M......W. &h|
00000180  10 bf 1e 24 74 05 5b 3b  e5 e6 d8 c7 a3 76 ed d6  |...$t.[;.....v..|
00000190  68 fb 65 35 0b 2f 85 11  0b 65 28 b0 18 b8 bb 1b  |h.e5./...e(.....|
000001a0  ad 49 66 ca 9f 65 08 64  a0 ad 5f 62 e6 56 ec bc  |.If..e.d.._b.V..|
000001b0  a5 53 3c a9 ac 86 c6 3d  f0 e2 21 23 18 b7 00 fe  |.S<....=..!#....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Sorry, some words are in Finnish.

---

### Post by tom4everitt on 2011-08-21
> **Robboti said:**
> Windows shows up on grub, but I'm not able to boot to it. I've tried to press almost every possible button on startup (Not quite sure if all), but Can't get into boot menu and I'm too tired to keep trying. Perhaps tomorrow.
Thank you anyway.

Usually the boot screen will tell you which button to press - press it repeatedly until you get the boot menu. 

If the boot screen doesn't tell you that, what kind of computer/motherboard do you have? Probably you could just google "how to get into boot menu with computer type x" or similar...

Also, if you can get into BIOS, that also works. In BIOS you can set the boot order so the external cd drive comes first. Just look around in the settings, and you should find it.

---

### Post by Robboti on 2011-08-21
Now I can get in to boot menu (I had to check something like "show f12 boot menu on start up" in bios) but turned out the Recovery CD my dad had, had "Disc 2" on it and it needs to be "disc 1", I guess, since I can't boot it. Well... off to search it.


EDIT: I found it, plugged it in and booted to it. After a while it complained something about drivers (Altough DVD-drive works fine, when I restarted and tried it on Ubuntu)and the screen turned red and said something like "Please insert disc 1" and disc one was already in. I also tried inserting disc 2, but it didn't help.

---

### Post by oldfred on 2011-08-21
Recovery DVDs are usually vendor images of the hard drive and only for one system. You need a windows repairCD. Sometimes you can get into windows repair by pressing f8 just after clicking on windows in grub, but you have to be quick. Some have had to try several times to get it to work.

If you have access to another windows computer you can make a repair CD that will work. It should be the same version 32bit or 64bit. But I used a win7 repairUSB to run chkdsk on my XP. But then had to rewrite the partition boot sector as it updated to win7 from XP.


Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Robboti on 2011-08-21
> **oldfred said:**
> Recovery DVDs are usually vendor images of the hard drive and only for one system. You need a windows repairCD. Sometimes you can get into windows repair by pressing f8 just after clicking on windows in grub, but you have to be quick. Some have had to try several times to get it to work.

If you have access to another windows computer you can make a repair CD that will work. It should be the same version 32bit or 64bit. But I used a win7 repairUSB to run chkdsk on my XP. But then had to rewrite the partition boot sector as it updated to win7 from XP.


Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I might sound stupid, but do I have to have the recovery disc in tray when I press f8?

---

### Post by oldfred on 2011-08-21
If it is just a recovery disk, all it does is reinstall.

You would not need recovery disk in CD. But if it is a repair disk then you can boot it direct. The f8  is only to try to get into the internal windows recovery before it does not boot. But even that does not always work and it is always best to have a Windows repairCD and a Ubuntu liveCD of the current version installed. I also usually have several other repairCd just to be able to boot if necessary.

---

### Post by Robboti on 2011-08-22
Grub had and option called Windows Recovery Enviroment and I was able to go there, but I have no idea what should I do there. It looks something like this 
[IMG]http://apcmag.com/site/wp-content/uploads/2006/08/DisableDriverSignatureReq.png[/IMG]
 I have already tried Start Windows Normally and Last Known Good Configuration, but they didn't work. Can I do something in WRE in order to fix this problem?

EDIT: and when I try to boot Safe mode, it starts loading files from Windows/system32/drivers/ but stops after disk.sys.

---

### Post by oldfred on 2011-08-22
How did you get that screen? It looks like a standard windows boot screen when you have problems.

---

### Post by Dabaizki on 2011-08-22
> **Robboti said:**
> Grub had and option called Windows Recovery Enviroment and I was able to go there, but I have no idea what should I do there. It looks something like this 
[IMG]http://apcmag.com/site/wp-content/uploads/2006/08/DisableDriverSignatureReq.png[/IMG]
 I have already tried Start Windows Normally and Last Known Good Configuration, but they didn't work. Can I do something in WRE in order to fix this problem?

EDIT: and when I try to boot Safe mode, it starts loading files from Windows/system32/drivers/ but stops after disk.sys.

Can you log in the Windows 7 on sdc? If you can ,then run this program,a cmd window,just type any key,it will repair the boot loader automatic.

Download adress: 
bcdautofix:
[http://58.248.245.160/down_group6/M00/24/EA/d5NqT0t8yRQAAAAAAAOGTXKBKwI7268738/bcdautofix_v1.0.5_.rar?k=_h6Fl2U8KJXYc8guszcvbA&t=1314045415&u=124.130.161.141@1508609@dy3bk30v&file=bcdautofix_v1.0.5_.rar](http://58.248.245.160/down_group6/M00/24/EA/d5NqT0t8yRQAAAAAAAOGTXKBKwI7268738/bcdautofix_v1.0.5_.rar?k=_h6Fl2U8KJXYc8guszcvbA&t=1314045415&u=124.130.161.141@1508609@dy3bk30v&file=bcdautofix_v1.0.5_.rar)

Good luck. It's just  something wrong on the bootloader . Don't give up.

---

### Post by Robboti on 2011-08-22
> **oldfred said:**
> How did you get that screen? It looks like a standard windows boot screen when you have problems.
As I said, there was an option on Grub menu called Windows Recovery Enviroment and I chose it. Then it said "Windows is loading files" and for some reason it froze unless I pressed the f8 button right after I had chose it. Then that screen popped up.

> **Dabaizki said:**
> Can you log in the Windows 7 on sdc? If you can  ,then run this program,a cmd window,just type any key,it will repair  the boot loader automatic.
Well 1st of all, I have XP, not 7.
And second, I can't log in (if that means, that can I start Windows up), that's the problem in the first case (I think). But thanks for the effort. :)

---

### Post by oldfred on 2011-08-22
If you then go to command prompt you can run chkdsk and other repairs to see if that fixes it. Often you have to run chkdsk multiple times until there are no errors.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by Robboti on 2011-08-23
> **oldfred said:**
> If you then go to command prompt you can run chkdsk and other repairs to see if that fixes it. Often you have to run chkdsk multiple times until there are no errors.


Do you mean Safe mode with Command Prompt? If I choose it, it acts like regular safe mode (as I mentioned above). It says "Windows is loading files" and files start running, but after drive.sys, it freezes.

---

### Post by Robboti on 2011-09-06
Aaand **** it. I moved to Ubuntu (Without Removing Windows partition, since I already had Ubuntu installed). Let's just hope it works without bigger problems.

In other words: "Bump"

---

### Post by oldfred on 2011-09-06
Did you ever get safe mode command line to work? That or a Windows XP CD to run the repair commands posted before. You seem to have been using a windows 7 boot partition sdc1 to boot XP. The XP sdc2  partition has all sorts of errors that chkdsk & fixboot should repair.

---

### Post by Robboti on 2011-09-07
> **oldfred said:**
> Did you ever get safe mode command line to work? That or a Windows XP CD to run the repair commands posted before. You seem to have been using a windows 7 boot partition sdc1 to boot XP. The XP sdc2  partition has all sorts of errors that chkdsk & fixboot should repair.
No, I haven't been able to get in safe mod at all. But I bet the problem can be fixed using the methods mentioned here.
One thing is for sure: the next time I buy a laptop, I make sure it comes with a recovery disk... and use it a way it never needs one.
Would changing boot partition with Gparted help? Just asking before I try and brick the whole machine even more.

---

### Post by oldfred on 2011-09-07
Windows repairs only work on the boot partition (active partition in windows). You can use a Windows repairCD to set the active partition also.

---

### Post by Robboti on 2012-02-25
Problem solved. I installed Windows 7 to replace Windows XP

---

