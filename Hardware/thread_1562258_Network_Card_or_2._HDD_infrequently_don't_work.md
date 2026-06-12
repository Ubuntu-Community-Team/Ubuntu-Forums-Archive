---
title: "Network Card or 2. HDD *infrequently* don't work"
date: 2010-08-27
forum: Hardware
---

### Post by nZain on 2010-08-27
Hi Comunity,

this is going to be a challenge, I guess. My desktop computer is half a year old and from time to time (since I bought it), the network card or one harddrive is not working. It happens infrequently without changing anything on the system. Also, this does not only affect Ubuntu, but the Win7 installation, too.

**Why this Thread?**
First of all, this seems to be a hardware issue and it's the vendors responsibility to fix such problems, if they occure within 2 years (waranty). Unfortunately, the problem happens so infrequently and a reboot does usually suffice. So everytime I bring my computer to the shop, everything works fine and they can't find the problem. This happened 3 times now: the first time they gave me a new hdd+cables. Nothing changed. Second time, they exchanged the motherbord (any hey, I thoght that should fix it)... but the issue remains. Third time, they told me that they had the issue I described - yay, finally they believe me. Unfortunately, the reinstalled the network driver on Win7 and told me that it works now. Linux is my problem. Ehhh. You guess right, nothing has really changed... both issues remain on Ubuntu as well as Win. So why this thread? *I hope that some hardcore cracks are able to help me track down the problem with the power of open source* (win would tell me to ask my network admin :p).

**System & Components**
I'm running Ubuntu Lucid 64bit (as well as win7).

[LIST=1]
[*]Motherboard: Gigabyte GA-P55A-UD3 (onboard LAN)
[*]Harddisks are both Western Digital (Caviar Blue Series), first one with 320GB (WD3200AAJS-00L7A0), second one 500GB (WD5000AAKS-00UU3A0).
[*]more details on request
[/LIST]

**Detailed Problem**
1. Sometimes (!) the network (LAN) does not work although drivers/card seem to be ok. Both linux/win tell me that no cable is connected. However, I tested serveral cables (also with other computers) and all are ok.
2a. [with the first mainboard] Sometimes (!) the second harddisk is not found as it was not even there (no udev entry, win just does not show it)
2b. [with the new mainboard] It happens ca. every 3. boot that I'm dropped to a shell with the message:
> Gave up waiting for root device Common problems:
  (...)
ALERT! /dev/disk/by-uuid/cbae7bc5-b92e-4db8-ab5e-5c668d067ffc does not exist. Dropping to a shell!
So it seems with the new mainboard the first hdd (at least the ubuntu root partition which corresponds to that uuid) is not found.

So, how would I start to track down this (these) problems?
Thanks in advance
  nZain

---

### Post by nZain on 2010-08-27
For those interested, here is the output of the bootinfo script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 320.1 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   312,638,488   312,431,641   7 HPFS/NTFS
/dev/sda3         312,639,486   625,141,759   312,502,274   5 Extended
/dev/sda5         312,639,488   320,450,559     7,811,072  82 Linux swap / Solaris
/dev/sda6         320,452,608   625,141,759   304,689,152  83 Linux


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        669250EA9250C06B                       ntfs       Windows7-bootloader           
/dev/sda2        56DA626BDA624779                       ntfs       Windows7                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        878e2d97-7349-484c-a9bb-c4cff272085f   swap                                     
/dev/sda6        cbae7bc5-b92e-4db8-ab5e-5c668d067ffc   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1087DB9B618B193A                       ntfs       Datengrab-500GB               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /automnt/Datengrab-500GB fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set cbae7bc5-b92e-4db8-ab5e-5c668d067ffc
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set cbae7bc5-b92e-4db8-ab5e-5c668d067ffc
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set cbae7bc5-b92e-4db8-ab5e-5c668d067ffc
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbae7bc5-b92e-4db8-ab5e-5c668d067ffc ro   quiet
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set cbae7bc5-b92e-4db8-ab5e-5c668d067ffc
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbae7bc5-b92e-4db8-ab5e-5c668d067ffc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set cbae7bc5-b92e-4db8-ab5e-5c668d067ffc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set cbae7bc5-b92e-4db8-ab5e-5c668d067ffc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 669250ea9250c06b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc  proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda6 during installation
UUID=cbae7bc5-b92e-4db8-ab5e-5c668d067ffc  /      ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=878e2d97-7349-484c-a9bb-c4cff272085f  none   swap  sw                   0  0  


=================== sda6: Location of files loaded by Grub: ===================


 312.3GB: boot/grub/core.img
 211.7GB: boot/grub/grub.cfg
 312.5GB: boot/initrd.img-2.6.32-24-generic
 312.5GB: boot/vmlinuz-2.6.32-24-generic
 312.5GB: initrd.img
 312.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  98 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |............@...|
00000010  00 00 00 00 00 00 00 00  14 00 14 00 28 00 38 00  |............(.8.|
00000020  60 00 38 00 b0 03 01 00  00 00 30 05 00 00 08 00  |`.8.......0.....|
00000030  29 00 00 00 00 00 00 00  03 dc 09 00 00 00 00 00  |)...............|
00000040  bc 97 61 fb a7 d1 ca 01  3c a4 44 1c aa d1 ca 01  |..a.....<.D.....|
00000050  3c a4 44 1c aa d1 ca 01  bc 97 61 fb a7 d1 ca 01  |<.D.......a.....|
00000060  00 d0 26 00 00 00 00 00  1f ca 26 00 00 00 00 00  |..&.......&.....|
00000070  20 00 00 00 00 00 00 00  bc 97 61 fb a7 d1 ca 01  | .........a.....|
00000080  3c a4 44 1c aa d1 ca 01  3c a4 44 1c aa d1 ca 01  |<.D.....<.D.....|
00000090  bc 97 61 fb a7 d1 ca 01  00 d0 26 00 00 00 00 00  |..a.......&.....|
000000a0  5f ca 26 00 00 00 00 00  20 00 00 00 00 00 00 00  |_.&..... .......|
000000b0  96 a5 22 0b 00 00 00 00  7d a5 22 0b 00 00 00 00  |..".....}.".....|
000000c0  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
000000d0  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
000000e0  1b 00 01 00 28 00 00 00  28 00 00 00 18 00 00 00  |....(...(.......|
000000f0  00 00 00 00 00 00 02 00  00 00 00 00 00 00 00 00  |................|
00000100  03 00 00 00 80 f8 ff ff  a1 a5 22 0b 00 00 00 00  |..........".....|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  38 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |8...........@...|
00000130  00 00 00 00 00 00 00 00  07 00 07 00 28 00 08 00  |............(...|
00000140  30 00 08 00 18 00 01 00  38 00 58 00 04 00 02 00  |0.......8.X.....|
00000150  4a 39 00 00 00 00 00 00  4a 39 0c 00 00 00 00 00  |J9......J9......|
00000160  f0 95 d4 00 00 00 00 00  90 95 d4 00 00 00 00 00  |................|
00000170  ae a5 22 0b 00 00 00 00  a1 a5 22 0b 00 00 00 00  |..".......".....|
00000180  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
00000190  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
000001a0  1b 00 01 00 28 00 00 00  28 00 00 00 18 00 00 00  |....(...(.......|
000001b0  00 00 00 00 00 00 02 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 77 00 00 fe  |...........0w...|
000001d0  ff ff 05 fe ff ff 02 30  77 00 00 38 29 12 00 00  |.......0w..8)...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by nZain on 2010-08-28
no ideas? If its neither the mainboard, nor the hdd... what component could it be? Or is this a software problem... I don't think so.

---

### Post by nZain on 2010-08-31
Come on - there must be a crack out there... someone that knows more than me (which is not that difficult at all) :popcorn:

---

