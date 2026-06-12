---
title: "Boot fails (freeze) when USBHDD not plugged in"
date: 2010-12-02
forum: Hardware
---

### Post by darius.k on 2010-12-02
Hello everyone,

I've got a boot problem on my laptop (Lenovo 3000 N200). I got a USB HDD (WD MyBook) at home, which is mounted via /etc/fstab and its UUID. Furthermore I've got several mounts in fstab that bind directories on the HDD to directories in my home folder.

When I am trying to boot the laptop, when I'm somewhere else and the HDD is not plugged in, it doesn't boot. More exactly it stops booting at some point and freezes. The last thing I see on the screen is: "conflicting fb hw usage: inteldrmfb vs VEGA VGA". Maybe this gives you an idea where it stops, even though this is not related to my problem, as far as I can tell.

Maybe someone of you can help me?

This is my /etc/fstab minus the header comments:
```
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2ec9b6ec-c303-4cef-bdb4-d1258e436736 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24ab5bf5-1b97-4740-895a-c44a6100dee2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#UUID=44DC373BDC372698 /media/MyBook/ ntfs user 0 0
/home/darius/Downloads/Dropbox/Photos		/home/darius/Bilder	none	bind	0	0
/home/darius/Downloads/Dropbox/Dokumente	/home/darius/Dokumente	none	bind	0	0
/home/darius/Downloads/Dropbox/scripts		/home/darius/scripts	none	bind	0	0
/home/darius/Downloads/Dropbox/Vorlagen		/home/darius/Vorlagen	none	bind	0	0
#/media/MyBook/Videos/Comedy	/home/darius/Videos/Comedy/	none	bind	0	0
#/media/MyBook/Videos/Dokumentationen	/home/darius/Videos/Dokumentationen/	none	bind	0	0
#/media/MyBook/Videos/Filme	/home/darius/Videos/Filme/	none	bind	0	0
#/media/MyBook/Videos/Musik	/home/darius/Videos/Musik/	none	bind	0	0
#/media/MyBook/Musik	/home/darius/Audios/Musik/	none	bind	0	0
#/media/MyBook/Hörbücher	/home/darius/Audios/Hörbücher/	none	bind	0	0
```

---

### Post by wilee-nilee on 2010-12-02
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by darius.k on 2010-12-02
Here are the results, I did it with the USB HDD plugged in and my normal linux install booted.

Thank you for your help.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 286271 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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

/dev/sda1    *             63   612,365,669   612,365,607  83 Linux
/dev/sda2         612,365,670   625,137,344    12,771,675   5 Extended
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2ec9b6ec-c303-4cef-bdb4-d1258e436736   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        44DC373BDC372698                       ntfs       MyBook                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/MyBook_           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
set locale_dir=($root)/boot/grub/locale
set lang=de
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
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=2ec9b6ec-c303-4cef-bdb4-d1258e436736 ro  vga=792  video=vesafb:off quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=2ec9b6ec-c303-4cef-bdb4-d1258e436736 ro single  vga=792
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2ec9b6ec-c303-4cef-bdb4-d1258e436736 ro  vga=792  video=vesafb:off quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2ec9b6ec-c303-4cef-bdb4-d1258e436736 ro single  vga=792
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2ec9b6ec-c303-4cef-bdb4-d1258e436736
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2ec9b6ec-c303-4cef-bdb4-d1258e436736 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24ab5bf5-1b97-4740-895a-c44a6100dee2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#UUID=44DC373BDC372698 /media/MyBook/ ntfs user 0 0
/home/darius/Downloads/Dropbox/Photos		/home/darius/Bilder	none	bind	0	0
/home/darius/Downloads/Dropbox/Dokumente	/home/darius/Dokumente	none	bind	0	0
/home/darius/Downloads/Dropbox/scripts		/home/darius/scripts	none	bind	0	0
/home/darius/Downloads/Dropbox/Vorlagen		/home/darius/Vorlagen	none	bind	0	0
#/media/MyBook/Videos/Comedy	/home/darius/Videos/Comedy/	none	bind	0	0
#/media/MyBook/Videos/Dokumentationen	/home/darius/Videos/Dokumentationen/	none	bind	0	0
#/media/MyBook/Videos/Filme	/home/darius/Videos/Filme/	none	bind	0	0
#/media/MyBook/Videos/Musik	/home/darius/Videos/Musik/	none	bind	0	0
#/media/MyBook/Musik	/home/darius/Audios/Musik/	none	bind	0	0
#/media/MyBook/Hörbücher	/home/darius/Audios/Hörbücher/	none	bind	0	0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  77.4GB: boot/grub/grub.cfg
  62.3GB: boot/initrd.img-2.6.31-19-generic
 220.9GB: boot/initrd.img-2.6.35-22-generic
 142.5GB: boot/initrd.img-2.6.35-23-generic
  83.8GB: boot/vmlinuz-2.6.35-22-generic
 139.1GB: boot/vmlinuz-2.6.35-23-generic
 142.5GB: initrd.img
 220.9GB: initrd.img.old
 139.1GB: vmlinuz
  83.8GB: vmlinuz.old
```

---

### Post by searchfgold6789 on 2010-12-02
If you comment out the single entry in your fstab that refers to your USB HD, and leave all the other ones that -bind it, maybe mountall will handle the drive when it is plugged in, and fstab will ignore it if it is not plugged in... Maybe...
The newer version of ubuntu will give you an option to skip mounting if it sees any errors.

---

### Post by darius.k on 2010-12-02
I will try that, searchfgold, thank you.
The reason that I manually mount the USB HDD is that I have had problems with the automount ignoring the regular "MyBook" mountpoint and creating "MyBook_". However I will try it and report back, but that's gotta wait until after todays christmas shopping. ;)

---

### Post by darius.k on 2010-12-06
I tried removing the fstab mounting of MyBook and letting automount do it, and only left the binds in. But unfortunatly automount seems to take action only after the fstab and that leads to ubuntu not mounting the binds, because it can't find the source directories.

Maybe I should do the mounting via a script on login? I will try that.

Thank you for your help anyways, searchfgold! :)

Any other ideas?

---

### Post by darius.k on 2010-12-07
Using a script on login to do the mounting is not working since mounting has do be done by root.

Anyone having any other ideas, please?

---

