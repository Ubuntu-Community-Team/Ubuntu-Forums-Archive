---
title: "Can't mount Mac-partition!"
date: 2011-01-03
forum: Hardware
---

### Post by MatthiasL on 2011-01-03
Hi everybody,

I have been dual-booting for a while now,
and yesterday, I tried to save a file from a bad external hard disk with dd_rescue.
I sent the file to be saved on my mac-partition, and I believe that's where it went wrong.
I can no longer boot Mac OS X, nor can I mount the partition from ubuntu.

/etc/fstab looks like this;

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc     nodev,noexec,nosuid  0  0  
# / was on /dev/sda3 during installation
UUID=a3e78279-9c3b-4e0d-85b6-55f87b2c49e3  /                 ext3     errors=remount-ro    0  1  
# swap was on /dev/sda4 during installation
UUID=c6625af4-f583-40df-a7f1-85a5f471fab6  none              swap     sw                   0  0  
/dev/sda2                                  /media/Macintosh  hfsplus  users,user,owner     0  0  
/dev/sda1                                  /media/sda1       vfat     noauto               0  0  
/dev/sdb2                                  /media/sdb2       hfsplus  defaults             0  0  



and the result of fdisk -l is this;

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       17165   137667268   af  HFS / HFS+
/dev/sda3   *       17181       19005    14648320   83  Linux
/dev/sda4           19005       19458     3638272   82  Linux swap / Solaris


It is /dev/sda2 I'm trying to mount. As an error, I get this;

Error mounting: mount exited with exit code 1: helper failed with:
mount: /dev/sda2: can't read superblock


Any help?
I really need the content of that partition for school...

Thanks

---

### Post by MatthiasL on 2011-01-03
oh, and here are the results of the boot info script, if that helps...
As you can see, /dev/sda2 can't be mounted because he can't read superblock.
No idea what that means, honestly....

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

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
    Mounting failed:
mount: /dev/sda2: can't read superblock

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 285972736 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640   275,744,175   275,334,536  af HFS
/dev/sda3    *    276,006,912   305,303,551    29,296,640  83 Linux
/dev/sda4         305,303,552   312,580,095     7,276,544  82 Linux swap / Solaris


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   275,744,175   275,334,536 HFS+
/dev/sda3     276,006,912   305,303,551    29,296,640 Linux or Data
/dev/sda4     305,303,552   312,580,095     7,276,544 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70D6-1701                              vfat       EFI                           
/dev/sda2        2c0d0ff9-ae3a-357b-9c2c-ee9c42cda2fb   hfsplus                                  
/dev/sda3        a3e78279-9c3b-4e0d-85b6-55f87b2c49e3   ext3                                     
/dev/sda4        c6625af4-f583-40df-a7f1-85a5f471fab6   swap                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro,commit=0)


=========================== sda3/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a3e78279-9c3b-4e0d-85b6-55f87b2c49e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a3e78279-9c3b-4e0d-85b6-55f87b2c49e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a3e78279-9c3b-4e0d-85b6-55f87b2c49e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a3e78279-9c3b-4e0d-85b6-55f87b2c49e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set a3e78279-9c3b-4e0d-85b6-55f87b2c49e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set 53d4addee5227991
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 53d4addee5227991 uuid
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
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
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
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set 53d4addee5227991
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 53d4addee5227991 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
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
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc     nodev,noexec,nosuid  0  0  
# / was on /dev/sda3 during installation
UUID=a3e78279-9c3b-4e0d-85b6-55f87b2c49e3  /                 ext3     errors=remount-ro    0  1  
# swap was on /dev/sda4 during installation
UUID=c6625af4-f583-40df-a7f1-85a5f471fab6  none              swap     sw                   0  0  
/dev/sda2                                  /media/Macintosh  hfsplus  users,user,owner     0  0  
/dev/sda1                                  /media/sda1       vfat     noauto               0  0  
/dev/sdb2                                  /media/sdb2       hfsplus  defaults             0  0  

=================== sda3: Location of files loaded by Grub: ===================


 146.4GB: boot/grub/core.img
 146.5GB: boot/grub/grub.cfg
 146.4GB: boot/initrd.img-2.6.35-22-generic
 146.5GB: boot/initrd.img-2.6.35-23-generic
 146.5GB: boot/vmlinuz-2.6.35-22-generic
 146.5GB: boot/vmlinuz-2.6.35-23-generic
 146.5GB: initrd.img
 146.4GB: initrd.img.old
 146.5GB: vmlinuz
 146.5GB: vmlinuz.old
```


Thanks again for any help.

---

