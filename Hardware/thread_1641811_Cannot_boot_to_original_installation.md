---
title: "Cannot boot to original installation"
date: 2010-12-09
forum: Hardware
---

### Post by tomasdaly on 2010-12-09
I installed a Zotac GForce 6200 card on my computer, but could not change the resolution, so I uninstalled the Nvidia drivers and removed the card. In the process I messed up grub and X.org server
After that I could not boot into 10.04., so  I installed another instance on Ubuntu on another small partition in order to access my files. That worked fine and I was able to back up all files from the bad partition.
When I try to boot into the bad partition I receive the following errors:
vga=791 is deprecated. Use set gfxpayload=text before linux command lines
Error: Couldn't read file
Error: You need to load the kernel first
I have researched this problem on Google and tried many solutions, but still cannot boot into the bad partition.
I tried to attached the results file from boot_info_script but file is .5KB over size limit so here is file:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

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

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb5 starts at sector 126.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   265,820,159   265,818,112  83 Linux
/dev/sda2         284,266,494   312,580,095    28,313,602   5 Extended
/dev/sda5         306,952,192   312,580,095     5,627,904  82 Linux swap / Solaris
/dev/sda6         284,266,496   305,893,375    21,626,880  83 Linux
/dev/sda7         305,895,424   306,937,855     1,042,432  82 Linux swap / Solaris
/dev/sda3         265,820,160   284,265,770    18,445,611  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    39,102,209    39,102,147   5 Extended
/dev/sdb5                 126    39,102,209    39,102,084   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24e18525-792f-4021-ad42-4213dbf37f8b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        29d90afc-2f8c-4e4a-86c8-8dfe019f26c9   ext4                                     
/dev/sda5        079f1a8f-e19a-4d25-92fd-b1a31d45d115   swap                                     
/dev/sda6        40f0fada-26f9-4c08-b874-626e29355a33   ext4                                     
/dev/sda7        c0d27cc1-cc0f-436a-8d50-b6585ef32287   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        BDF6-85AD                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/24e18525-792f-4021-ad42-4213dbf37f8b ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro vga=d791  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro single vga=d791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro vga=d791  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro single vga=d791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro vga=d791  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro single vga=d791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=24e18525-792f-4021-ad42-4213dbf37f8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=079f1a8f-e19a-4d25-92fd-b1a31d45d115 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 124.6GB: boot/grub/core.img
  99.2GB: boot/grub/grub.cfg
 124.9GB: boot/initrd.img-2.6.32-24-generic
 125.2GB: boot/initrd.img-2.6.32-25-generic
 125.3GB: boot/initrd.img-2.6.32-26-generic
 124.7GB: boot/vmlinuz-2.6.32-24-generic
 125.0GB: boot/vmlinuz-2.6.32-25-generic
 125.2GB: boot/vmlinuz-2.6.32-26-generic
 125.3GB: initrd.img
 125.2GB: initrd.img.old
 125.2GB: vmlinuz
 125.0GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set 40f0fada-26f9-4c08-b874-626e29355a33
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
search --no-floppy --fs-uuid --set 40f0fada-26f9-4c08-b874-626e29355a33
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 40f0fada-26f9-4c08-b874-626e29355a33
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=40f0fada-26f9-4c08-b874-626e29355a33 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 40f0fada-26f9-4c08-b874-626e29355a33
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=40f0fada-26f9-4c08-b874-626e29355a33 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 40f0fada-26f9-4c08-b874-626e29355a33
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 40f0fada-26f9-4c08-b874-626e29355a33
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro vga=d791 quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro single vga=d791
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro vga=d791 quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro single vga=d791
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro vga=d791 quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 24e18525-792f-4021-ad42-4213dbf37f8b
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=24e18525-792f-4021-ad42-4213dbf37f8b ro single vga=d791
    initrd /boot/initrd.img-2.6.32-24-generic
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=40f0fada-26f9-4c08-b874-626e29355a33 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c0d27cc1-cc0f-436a-8d50-b6585ef32287 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 150.5GB: boot/grub/core.img
 150.5GB: boot/grub/grub.cfg
 154.8GB: boot/initrd.img-2.6.32-24-generic
 146.0GB: boot/vmlinuz-2.6.32-24-generic
 145.5GB: boot/vmlinuz-2.6.32-24-generic.dpkg-new
 154.8GB: initrd.img
 146.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  13 de 76 fa d8 56 fb 7b  da 87 ac df 97 30 a5 a1  |..v..V.{.....0..|
00000010  3b 0d cd 0e 67 72 3e 99  ee 67 ff 2a c9 ae 5f 21  |;...gr>..g.*.._!|
00000020  eb 6c d8 b1 79 30 31 a1  88 83 72 ad 60 9c 75 ba  |.l..y01...r.`.u.|
00000030  4d ae af 4a 00 02 6e c0  da e6 cd c2 64 1e 44 00  |M..J..n.....d.D.|
00000040  92 32 32 23 30 29 47 33  0c 0f 45 b2 a0 74 16 8d  |.22#0)G3..E..t..|
00000050  0d 55 73 20 18 68 36 6e  1f 77 50 d9 6e 4e a0 c3  |.Us .h6n.wP.nN..|
00000060  17 5b 4d e1 da cc 3e 6a  ca ae 46 13 63 a9 b5 b2  |.[M...>j..F.c...|
00000070  44 f2 b0 c2 81 44 4c ef  ea ea 1b 94 7b d5 31 d8  |D....DL.....{.1.|
00000080  17 77 cf c1 1d 2c 67 5a  ff fb 92 64 e6 8c c3 58  |.w...,gZ...d...X|
00000090  35 54 1b 6c 1d 20 49 c6  1a e3 61 23 3e 0d ad 03  |5T.l. I...a#>...|
000000a0  50 6e 30 52 c1 5a 1a 6a  cd 86 0d e0 7a f5 44 ff  |Pn0R.Z.j....z.D.|
000000b0  a3 05 27 28 7f 3f 4f fa  a0 c8 2f 4b 41 a9 ae 15  |..'(.?O.../KA...|
000000c0  bd c2 75 fd 35 57 f0 ef  fa 33 00 29 76 02 6c bc  |..u.5W...3.)v.l.|
000000d0  25 fa 14 19 72 01 ca 6d  18 0d 61 39 3f 80 f5 3e  |%...r..m..a9?..>|
000000e0  2c cf dd f3 e1 ca 3a 21  29 01 38 c5 94 a0 a8 85  |,.....:!).8.....|
000000f0  77 2d 2c a9 56 69 69 41  aa c9 e5 e7 64 50 89 73  |w-,.ViiA....dP.s|
00000100  6c 62 89 86 9c 05 69 26  09 49 12 48 74 7b 5c 60  |lb....i&.I.Ht{\`|
00000110  36 75 4b 31 73 9d fe a0  00 57 7e 02 d4 13 7f 9b  |6uK1s....W~.....|
00000120  cd 1a 0b 31 09 68 c4 41  13 05 0c 1b 60 08 11 f8  |...1.h.A....`...|
00000130  4b 76 b0 d6 66 03 88 52  0c e8 88 f2 88 30 ca 47  |Kv..f..R.....0.G|
00000140  65 c9 0d 0c f2 5a 98 89  02 31 44 a9 63 41 1e ad  |e....Z...1D.cA..|
00000150  ea f9 d7 2d e9 f9 a0 c1  9d f3 7e a4 76 db 0f 2b  |...-......~.v..+|
00000160  f4 20 66 62 bc 8b fe 9c  f0 45 35 e6 20 19 1a 91  |. fb.....E5. ...|
00000170  5e 4b f2 12 2c 06 31 47  bb fa f6 1f 9a 1e 71 ab  |^K..,.1G......q.|
00000180  01 6c 3f 5f 3f db 76 6d  f5 db 91 62 31 dc 35 c0  |.l?_?.vm...b1.5.|
00000190  1b f0 f6 bc 82 72 ce a8  00 81 73 cd 21 79 7a c3  |.....r....s.!yz.|
000001a0  22 b1 44 71 10 d9 56 bc  55 cf 10 ce 48 4e 2f ba  |".Dq..V.U...HN/.|
000001b0  38 8b c3 d6 75 65 ad 68  62 6b 8c 0c 82 f5 00 fe  |8...ue.hbk......|
000001c0  ff ff 82 fe ff ff 02 28  5a 01 00 e0 55 00 00 fe  |.......(Z...U...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 00 4a 01 00 00  |............J...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
I've reached the point where my only option appears to be to reinstall Ubuntu on the original large partition or to reformat that petition for data storage. Any suggestions will be greatly appreciated.

---

