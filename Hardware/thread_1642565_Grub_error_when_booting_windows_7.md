---
title: "Grub error when booting windows 7"
date: 2010-12-10
forum: Hardware
---

### Post by toothpick on 2010-12-10
I've just used the installer on a live disk of 32 bit Ubuntu 10.10 to make a persistant live usb.  My problem is that when I try to boot into my local drive now I get a no such drive grub boot error with a cursor waiting for a command.  Any thoughts?  I can still mount the drives with my live disk and see that all of the windows partitions and proper contents are still there.  Just can't boot into Windows.  Any help would be appreciated.

---

### Post by coffeecat on 2010-12-10
It sounds as though the installer has put grub on the mbr of the hard drive rather than the mbr of the live USB. Can you boot the live USB? And do you only have Windows on the internal drive of the computer, or do you have Ubuntu/Linux as well?

---

### Post by toothpick on 2010-12-10
No the usb won't boot.  The local drive is Windows 7 alone.  So I need to figure out a way to repair the MBR?

---

### Post by oldfred on 2010-12-10
With USB flash plugged in run this script, so we can be sure of what is installed where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by coffeecat on 2010-12-10
> **toothpick said:**
> So I need to figure out a way to repair the MBR?

Yes, most probably, although it would be a good idea to run the script oldfred has suggested - but you'll need to use the live CD since the USB is not bootable. Then we can be sure exactly what's going on.

A question while we await your RESULTS.txt. Did you remember to make a Windows 7 repair disc while Windows was still bootable? That's probably the best thing for repairing the MBR, but if you didn't we have other tricks up our collective sleeve.

---

### Post by toothpick on 2010-12-11
Here's the results.txt file.  Yes I have a rescue disk, however out of deference to your collective superior experience I'd be curious to hear what else is up your sleeve.  Noticing that none of the Windows partitions have any problems in the boot sector according to these results.  BTW pass on my thanks to  meierfra, that's a handy little script.     
```
 
 # Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128  27 Hidden HPFS/NTFS
/dev/sda2    *     29,362,176    29,566,975       204,800   7 HPFS/NTFS
/dev/sda3          29,566,976   625,139,711   595,572,736   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8000 MB, 8000110592 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    14,852,095    14,850,048  83 Linux
/dev/sdc2          14,854,142    15,624,191       770,050   5 Extended
/dev/sdc5          14,854,144    15,624,191       770,048  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DC80D88D80D86F8E                       ntfs       PQSERVICE                     
/dev/sda2        64C4D914C4D8E8F6                       ntfs       SYSTEM RESERVED               
/dev/sda3        F49CDA9B9CDA57A6                       ntfs       Acer                          
/dev/sda: PTTYPE="dos" 
/dev/sdc1        d1d846d7-6854-456c-98a9-03e517c00067   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        3248da21-a30c-40fa-a79a-0b08b1ab5eeb   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Acer              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/d1d846d7-6854-456c-98a9-03e517c00067 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set d1d846d7-6854-456c-98a9-03e517c00067
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set d1d846d7-6854-456c-98a9-03e517c00067
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set d1d846d7-6854-456c-98a9-03e517c00067
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d1d846d7-6854-456c-98a9-03e517c00067 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set d1d846d7-6854-456c-98a9-03e517c00067
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d1d846d7-6854-456c-98a9-03e517c00067 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set d1d846d7-6854-456c-98a9-03e517c00067
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set d1d846d7-6854-456c-98a9-03e517c00067
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dc80d88d80d86f8e
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 64c4d914c4d8e8f6
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=d1d846d7-6854-456c-98a9-03e517c00067 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=3248da21-a30c-40fa-a79a-0b08b1ab5eeb none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/core.img
   5.3GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-23-generic-pae
   2.6GB: boot/vmlinuz-2.6.35-23-generic-pae
   1.5GB: initrd.img
   2.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  d6 8e 5b 04 5c 6c 0a 03  14 03 22 d6 8f 18 06 3a  |..[.\l...."....:|
00000010  7c 0a 03 14 03 22 d6 ad  dd 02 44 90 0a 03 14 03  ||...."....D.....|
00000020  22 d6 ad dd 03 e8 89 09  03 14 02 22 d6 d8 08 78  |".........."...x|
00000030  7f 0a 03 14 03 22 d7 04  24 06 51 a2 0a 03 14 03  |....."..$.Q.....|
00000040  22 d7 10 bd 01 ce 53 0a  03 14 03 22 d7 10 bd 07  |".....S...."....|
00000050  3b 41 0a 03 14 03 22 d7  2d 6e 02 3a 67 0a 03 14  |;A....".-n.:g...|
00000060  03 22 d7 2d 6e 08 cb 92  0a 03 14 03 22 d7 42 9f  |.".-n.......".B.|
00000070  02 20 df 0a 03 14 03 22  d7 42 9f 02 2d 0f 0a 03  |. .....".B..-...|
00000080  14 03 22 d7 42 9f 02 2d  77 0a 03 14 03 22 d7 42  |..".B..-w....".B|
00000090  9f 02 2e c6 0a 03 14 03  22 d7 42 9f 02 39 95 0a  |........".B..9..|
000000a0  03 14 03 22 d7 52 ae 05  81 f9 0a 03 14 03 22 d7  |...".R........".|
000000b0  63 20 01 7b dc 0a 03 14  03 22 d7 df f0 05 e8 27  |c .{.....".....'|
000000c0  0a 03 14 03 22 d7 ee aa  02 cb 05 0a 03 14 03 22  |....".........."|
000000d0  d8 6e de 05 6f 5e 0a 03  14 03 22 d8 7b 9f 07 e4  |.n..o^....".{...|
000000e0  d4 0a 03 14 03 22 d8 82  67 04 23 f4 0a 03 14 03  |....."..g.#.....|
000000f0  22 d8 95 d5 02 06 f8 0a  03 14 03 22 d8 a4 e6 04  |".........."....|
00000100  1d 83 0a 03 14 03 22 d8  cd 34 05 c5 e3 0a 03 14  |......"..4......|
00000110  03 22 d8 e2 95 07 be 09  09 03 14 02 22 d8 e4 e4  |.".........."...|
00000120  37 61 0a 03 14 03 22 d8  f6 e9 04 62 83 0a 03 14  |7a...."....b....|
00000130  03 22 d9 38 70 01 9f 02  0a 03 14 03 22 d9 38 70  |.".8p.......".8p|
00000140  01 a5 12 0a 03 14 03 22  d9 38 70 08 e3 b7 0a 03  |.......".8p.....|
00000150  14 03 22 d9 8f 51 08 17  16 0a 03 14 03 22 da 47  |.."..Q.......".G|
00000160  32 05 e0 7c 0a 03 14 03  22 da 4b 0f 04 40 83 0a  |2..|....".K..@..|
00000170  03 14 03 22 da 58 55 06  47 87 0a 03 14 03 22 da  |...".XU.G.....".|
00000180  59 55 01 f1 70 0a 03 14  03 22 da 99 f8 07 16 85  |YU..p...."......|
00000190  0a 03 14 03 22 da cc a8  02 0b 95 0a 03 14 03 22  |....".........."|
000001a0  da cc a8 02 0b c2 0a 03  14 03 22 da cc a8 02 0b  |..........".....|
000001b0  cb 0a 03 14 03 22 db 5c  48 05 b0 55 0a 03 00 a0  |.....".\H..U....|
000001c0  c5 9c 82 8f c3 cc 02 00  00 00 00 c0 0b 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb#

```

---

### Post by drs305 on 2010-12-11
If you have a LiveCD, you can restore the ability to boot Windows by installing *lilo* or you can use a Windows repair disk to put the Windows back on the MBR of sda.

From the LiveCD, open a terminal and run these commands. You will get messages about fully installing lilo - just disregard them and only run the following *with sdc disconnected*:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

That should point the MBR to your sda boot partition, and start the Windows menu when the external is not plugged in when booting.

Now connect your external and confirm it is sdc. If it isn't sdc, change the designations below.

```
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
```

Do NOT put the partition number in the second command.

Now have your BIOS boot from the external first. It may be listed under Hard Drives - it depends on the BIOS.

If the external is plugged in, it will boot the Grub2 menu. If not, you will boot to Windows.

---

### Post by coffeecat on 2010-12-11
You can use the lilo method that drs305 posted for restoring the mbr. It works just fine. For the record, repairing the mbr from the Windows 7 install disc (or repair disc) involves going into the repair option, then to the command prompt and then:

```
bootrec /FixMbr
```

More here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by toothpick on 2010-12-11
Thanks all, worked like a charm.  Used the Lilo method recommended by drs305.

---

