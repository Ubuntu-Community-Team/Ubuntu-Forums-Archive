---
title: "can only boot from iso"
date: 2010-06-01
forum: Hardware
---

### Post by wrightsimmo80 on 2010-06-01
Hey all,
Hope someone can assist me with this headache. 
I have an HP dv5 1232  with vista home premium and recovery partition still intact ( i hope. )
I  installed ubuntu to a partition of the hdd  so on bootup I select  windows or ubuntu from the grub menu.

When I upgraded  to ubuntu  10.04 I chose to install grub file from the upgrade and followed  instruction to  tick all partitions to install it do ( maybe not the  best move?)
To begin grub detected all OS but would only load Ubuntu -  when I selected to load windows it sat in idle for a few seconds then  just booted ubuntu instead.

however ....
Since trying to  remedy this problem I have tried various methods of changing the mbr  (bootrec.exe,  bcdrebuild) but have actually gone back a step and now I  don't even get the grub menu.
I have a vista recovery iso burnt to  disc to get into command prompt, and can get into ubuntu via a live cd  for terminal, or a super grub disc,  however I've got no recovery or vista install discs to  work with. 


...My goal is to have vista and ubuntu 10 .04 happily booting from grub.
The partitions seem to be all intact  If I could  access the recovery partition and reinstall whole system to start over  this would be great.- or any other suggestions welcomed.

---

### Post by wrightsimmo80 on 2010-06-01
Looking at other post in similar situation this information got via " sudo bash ~/Desktop/boot_info_script*.sh" may be useful???

here is a paste of  the txt file

if there are any other commands that will determine fault please tell. 

cheers... 

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 234128901 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   233,617,229   233,617,167   7 HPFS/NTFS
/dev/sda2         758,005,760   781,416,447    23,410,688   7 HPFS/NTFS
/dev/sda3         233,617,230   757,994,894   524,377,665   5 Extended
/dev/sda5         233,617,293   365,125,319   131,508,027  83 Linux
/dev/sda6         740,050,353   757,994,894    17,944,542  82 Linux swap / Solaris
/dev/sda7         729,865,143   740,050,289    10,185,147  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        163AD1B13AD18DDD                       ntfs                                     
/dev/sda2        1C306F0C306EEC68                       ntfs       RECOVERY                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        141d6948-3fa3-4dad-996d-c950fe939903   ext4                                     
/dev/sda6        5bf1db98-5975-4433-a03d-3cae5c0733ae   swap                                     
/dev/sda7        0832728d-768f-4f61-8e33-decc46e3a794   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=141d6948-3fa3-4dad-996d-c950fe939903

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        141d6948-3fa3-4dad-996d-c950fe939903
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro splash  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=141d6948-3fa3-4dad-996d-c950fe939903 ro single splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 141d6948-3fa3-4dad-996d-c950fe939903
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 163ad1b13ad18ddd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1c306f0c306eec68
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=141d6948-3fa3-4dad-996d-c950fe939903 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5bf1db98-5975-4433-a03d-3cae5c0733ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 119.8GB: boot/grub/core.img
 120.6GB: boot/grub/grub.cfg
 139.1GB: boot/grub/menu.lst
 120.4GB: boot/initrd.img-2.6.31-14-generic
 120.6GB: boot/initrd.img-2.6.32-22-generic
 120.1GB: boot/vmlinuz-2.6.31-14-generic
 120.3GB: boot/vmlinuz-2.6.32-22-generic
 120.6GB: initrd.img
 120.4GB: initrd.img.old
 120.3GB: vmlinuz
 120.1GB: vmlinuz.old
```

---

