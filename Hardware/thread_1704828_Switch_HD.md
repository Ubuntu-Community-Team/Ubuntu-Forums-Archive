---
title: "Switch HD"
date: 2011-03-11
forum: Hardware
---

### Post by Jonker on 2011-03-11
Hi,
I have Ubuntu installed on a ext. HD. But the external HD is always /dev/sdb wheras the internal HD is /dev/sda. When I configure Grub, it gets installed on the internal HD. So I would like to make Ubuntu think that it is the primary HD (dev/sda). Is there a way of doing that?

---

### Post by Jonker on 2011-03-12
is this in the wrong forum, or is it impossible?

---

### Post by sikander3786 on 2011-03-13
We need you to connect all your hard disk (internal and external) then boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Then we will be able to give you exact commands for re-installation of Grub.

If you are confident to do it yourself, I hope this one will help you.

[http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html](http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html)

But I would still recommend to let us do the job for you.

---

### Post by Jonker on 2011-03-14
Hi,
I'll post the results here. But the point is, that the internal HDD is a /dev/sda and the external is /dev/sdb. I would like that the internal is /dev/sdb and the external is /dev/sdb. I would just like to virtualy swap them.

---

### Post by Jonker on 2011-03-14
OK, I managed to re-install Grub2. 

Here is the result of the script:
```
  [FONT=&quot]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 250.1 GByte, 250059350016 Byte
[/FONT][FONT=&quot]255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
[/FONT][FONT=&quot]Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   246,945,791   243,871,744   7 HPFS/NTFS
/dev/sda3         246,945,792   488,395,103   241,449,312   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 164.7 GByte, 164696555520 Byte
[/FONT][FONT=&quot]255 Köpfe, 63 Sektoren/Spur, 20023 Zylinder, zusammen 321672960 Sektoren
[/FONT][FONT=&quot]Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   308,533,247   308,531,200  83 Linux
/dev/sdb2         308,535,294   321,671,167    13,135,874   5 Extended
/dev/sdb5         308,535,296   321,671,167    13,135,872  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3206F52706F4ECAB                       ntfs       WinRE                         
/dev/sda2        22A466ECA466C241                       ntfs       Vista                         
/dev/sda3        BEF6251AF624D485                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        65d64a23-0b3f-4996-ac98-524886f846a0   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0562dcec-8a1f-4c73-a014-d195b4a79c67   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Vista             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=65d64a23-0b3f-4996-ac98-524886f846a0 ro vga=775 splash quiet  quiet profile
      initrd      /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      echo  'Loading Linux 2.6.35-28-generic-pae ...'
      linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=65d64a23-0b3f-4996-ac98-524886f846a0 ro single vga=775 splash quiet
      echo  'Loading initial ramdisk ...'
      initrd      /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      linux /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=65d64a23-0b3f-4996-ac98-524886f846a0 ro vga=775 splash quiet  quiet profile
      initrd      /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      echo  'Loading Linux 2.6.35-27-generic-pae ...'
      linux /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=65d64a23-0b3f-4996-ac98-524886f846a0 ro single vga=775 splash quiet
      echo  'Loading initial ramdisk ...'
      initrd      /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=65d64a23-0b3f-4996-ac98-524886f846a0 ro vga=775 splash quiet  quiet profile
      initrd      /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
      insmod part_msdos
      insmod ext2
      set root='(hd1,msdos1)'
      search --no-floppy --fs-uuid --set 65d64a23-0b3f-4996-ac98-524886f846a0
      linux16     /boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
      insmod part_msdos
      insmod ntfs
      set root='(hd0,msdos2)'
      search --no-floppy --fs-uuid --set 22a466eca466c241
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 144.0GB: boot/grub/core.img
 129.8GB: boot/grub/grub.cfg
  84.0GB: boot/initrd.img-2.6.35-27-generic-pae
   1.0GB: boot/initrd.img-2.6.35-28-generic-pae
 144.0GB: boot/vmlinuz-2.6.35-27-generic-pae
 144.0GB: boot/vmlinuz-2.6.35-28-generic-pae
   1.0GB: initrd.img
  84.0GB: initrd.img.old
 144.0GB: vmlinuz
 144.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  5f 12 dd cf ae dc b0 0b  f2 27 19 af 43 ff 00 84  |_........'..C...|
[/FONT][FONT=&quot]00000010  26 ea d2 46 8e 79 22 8c  8e c0 96 fd 71 5d 3c da  |&..F.y".....q]<.|
00000020  68 73 3d 59 e3 93 da c7  1a 90 53 3c 1e 7d 6b b1  |hs=Y......S<.}k.|
00000030  d7 74 88 ad 98 82 58 9e  15 46 38 a7 06 de fb 8e  |.t....X..F8.....|
00000040  c7 87 6b 97 32 2b 8e 78  38 15 df db f8 63 49 b8  |..k.2+.x8....cI.|
00000050  75 fb 54 06 45 04 9c 12  71 5a 5f b8 2d 74 47 80  |u.T.E...qZ_.-tG.|
[/FONT][FONT=&quot]00000060  ea 73 89 77 a9 39 09 de  be 9e 3e 11 f0 b0 04 43  |.s.w.9....>....C|
00000070  14 4b fe c8 ed 47 b5 6b  44 85 ca fa 9f 19 b2 cf  |.K...G.kD.......|
00000080  73 9c f6 ce 31 d4 d7 d1  fa ee 8f a7 21 db 12 02  |s...1.......!...|
00000090  e2 ad 4d b5 62 1c 5b 47  c9 3e 20 d0 75 ab f8 76  |..M.b.[G.> .u..v|
000000a0  24 7c 00 72 4d 7d 15 f6  27 01 95 d7 8a d1 54 70  |$|.rM}..'.....Tp|
000000b0  1a 5a 1f 13 69 ff 00 08  75 9b e9 d4 ca c6 3c 72  |.Z..i...u.....<r|
000000c0  14 77 fc eb ec 8b a8 16  32 85 00 2c 7d 28 95 49  |.w......2..,}(.I|
000000d0  31 72 69 a9 e2 16 3f 01  34 ed 45 55 af 24 77 01  |1ri...?.4.EU.$w.|
000000e0  ba 67 fc 2b e8 cd 3a 5b  99 46 30 3d 78 eb 59 ba  |.g.+..:[.F0=x.Y.|
000000f0  d2 7a 5c b7 4d 35 a1 e7  7a 07 c2 af 07 e8 4c 56  |.z\.M5..z.....LV|
[/FONT][FONT=&quot]00000100  3b 24 2f fd fc 73 5e c1  69 6f 97 e4 61 9b 8a 89  |;$/..s^.io..a...|
[/FONT][FONT=&quot]00000110  56 69 6b a8 24 af b1 c5  5d f8 4e df 61 11 c4 a0  |Vik.$...].N.a...|
[/FONT][FONT=&quot]00000120  74 1c 57 a8 c9 6e e3 86  43 8e e0 54 f3 e9 72 dc  |t.W..n..C..T..r.|
00000130  1b 7b 1e 18 74 45 83 e6  60 15 47 18 af 44 bb b2  |.{..tE..`.G..D..|
[/FONT][FONT=&quot]00000140  50 e4 14 e9 49 55 62 51  57 d4 f1 ad 43 4f 49 54  |P...IUbQW...COIT|
00000150  95 24 d7 73 a8 58 ee 04  64 29 3d fb 0a d2 33 b8  |.$.s.X..d)=...3.|
00000160  59 a4 78 a4 96 d3 c4 c4  13 c7 5c f7 ae c6 fb 4a  |Y.x.......\....J|
00000170  55 56 dc 41 c0 38 c5 69  19 bb d8 56 5b 9c 23 ae  |UV.A.8.i...V[.#.|
00000180  fc 36 4f 1c ee a5 b9 b5  48 86 ed bd 78 f6 35 a3  |.6O.....H...x.5.|
00000190  be dd 09 b1 97 aa 9d c8  48 e8 b8 aa b7 52 f9 08  |........H....R..|
000001a0  49 39 c7 38 aa 8d 93 b0  49 a6 8e 26 fa 02 dc 03  |I9.8....I..&....|
000001b0  f7 b3 d6 b7 ee 31 71 cb  00 47 5a bb 69 72 00 fe  |.....1q..GZ.ir..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 c8 00 00 00  |...........p....|
[/FONT][FONT=&quot]000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


 [/FONT]
  
```But I still don't know, how to switch the HDD.

---

### Post by sikander3786 on 2011-03-15
That output looks pretty good and tells that Grub is installed properly. I hope you are booting successfully now?

How Ubuntu recognizes HDDs I think depends on the Bios detection. The master devices are listed first and the slaves later i.e, Master will be sda and Slave sdb. Most of the time, USB drives are detected after the IDEs or SATA one's.

If there is some way of achieving what you are after, I fear I can't be much helpful there. But can I ask, why you want your sdb to be detected as sda?

---

### Post by Jonker on 2011-03-15
Yes, I'am booting fine. 
I wan't to have /dev/sdb detected as /dev/sda because when I configure Grub and update with

```
sudo grub-update
```Grub gets installed again on the internal HDD :(

---

### Post by Jonker on 2011-03-16
Hello,

I think I found a solution for Grub 1, maby one can do the same thing in Grub 2. This code would be in the menu.lst. But I don't understand this code fully.

```

title Windows
     rootnoverify (hd1, 0)
     map (hd0) (hd1)
     map (hd1) (hd0)
     chainloader +1

```

---

### Post by sikander3786 on 2011-03-16
That is just a menu.lst entry for Windows and nothing more. It won't work with Grub2.

In any case, running sudo update-grub shouldn't install Grub to any location other than its originally configured one. It happens with Wubi installs but you've got a proper install of Ubuntu on its own separate HDD and partition so that shouldn't happen here.

I wonder if running 'grub-update' has some different impacts where the correct command is 'update-grub'. I don't have a testing PC right now where I could test your command. Or is it a typo?

And if we assume that Grub gets installed to the internal HDD somehow when you run the command, did you ever need to restore the Windows MBR?

I would also request some senior members to take a look at your problem, in case we are missing something.

---

### Post by drs305 on 2011-03-16
See if running the following command with your external connected and running the OS helps:

```
sudo dpkg-reconfigure grub-pc
```
Use the TAB key to highlight OK, add any kernel options you use in the second screen, and most importantly, in the third screen make sure only the external drive (not the internal and not the external partition) is selected. Use the space bar to add/remove the asterisk, then TAB to OK and press ENTER.

You will want to make sure the BIOS points to the external drive first in the boot order.

---

### Post by Jonker on 2011-03-16
@sikander:

- I'm very sorry, of course the command is 'update-grub'! 
- I had to install the Windows MBR already twice, once after the installation ( [http://ubuntuforums.org/showthread.php?t=1697219](http://ubuntuforums.org/showthread.php?t=1697219)) and once after a update ( I'm not sure, it was a Kernel update, but during the update I was using the Startup- Manager). But since then, I didn't run the 'update-grub', because it is a pain reinstalling it (Win MBR and Grub).

@drs305
I'll try it out and let you know about the result. I have the BIOS set up, that the USB device is before the internal Harddrive.

---

### Post by Jonker on 2011-03-16
Ok, the command worked fine. The screen shot shows the configuration as it was. But I haven't restarted yet... The second screen shot is the configuration to which I changed it. I hope this was correct.

---

### Post by Jonker on 2011-03-16
It worked, the startup worked!

---

### Post by drs305 on 2011-03-16
Yes, that looks good. It should now work the way you want.

Edit: Simulposts. Well, glad it's fixed. If you don't have any other questions/comments about this issue, would you please mark it SOLVED via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing !

---

### Post by Jonker on 2011-03-16
ok, thanks for helping!!

---

