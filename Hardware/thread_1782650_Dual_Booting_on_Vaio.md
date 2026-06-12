---
title: "Dual Booting on Vaio"
date: 2011-06-14
forum: Hardware
---

### Post by djab on 2011-06-14
I am trying to install the Ubuntu dual boot on my Sony Vaio CW laptop. I downloaded the DVD, burnt it to a DVD, booted up my computer to the DVD and installed it to work with Windows 7 as planned. However after installation, I shut my computer down and reboot it, expecting to be brought with a screen asking if I want to boot into Windows or Ubuntu. It does not ask me what to boot in and just boots into Windows just like Ubuntu was never installed. Is this something with the bootloader? How can I get dual booting to work? How can I boot into Ubuntu?

Thanks in advance!

---

### Post by Rubi1200 on 2011-06-15
Hi and welcome to the forums :-)

We need to get a better overview of where everything is on the system.

Please download and run the boot info script. There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by djab on 2011-06-15
I have uploaded the results file. Please let me know what I must do to get dual booting working. Thanks!

---

### Post by Rubi1200 on 2011-06-16
For some reason the GRUB bootloader wasn't installed.

Here is what you need to do from the LiveCD:

boot the computer choosing to try not install and at the desktop open a terminal.

Run these commands:

```
sudo mount /dev/sda6 /mnt

sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

When the command completes reboot the computer taking out the CD.

Back in Ubuntu, run this command to add Windows to the GRUB menu:

```
sudo update-grub

```

Let me know how it goes please.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    12,933,119    12,931,072  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     12,933,120    13,137,919       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          13,137,920   477,774,363   464,636,444   7 NTFS / exFAT / HPFS
/dev/sda4         477,775,870   625,141,759   147,365,890   5 Extended
/dev/sda5         616,923,136   625,141,759     8,218,624  82 Linux swap / Solaris
/dev/sda6         477,775,872   608,702,463   130,926,592  83 Linux
/dev/sda7         608,704,512   616,912,895     8,208,384  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0p1   0B5D-8E32                              vfat       
/dev/sda1        92A49B51A49B36A7                       ntfs       Recovery
/dev/sda2        E6487B0D487ADC2D                       ntfs       System Reserved
/dev/sda3        30447CD6447CA070                       ntfs       Windows
/dev/sda5        8efa7202-005b-477e-bf4f-3bf8fb768228   swap       
/dev/sda6        4fb5084c-5da3-433b-9e92-9b1e44e07ed6   ext4       
/dev/sda7        9be4ab3c-cb25-4993-bfa7-7662ff078c74   swap       

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4fb5084c-5da3-433b-9e92-9b1e44e07ed6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4fb5084c-5da3-433b-9e92-9b1e44e07ed6
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4fb5084c-5da3-433b-9e92-9b1e44e07ed6
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4fb5084c-5da3-433b-9e92-9b1e44e07ed6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4fb5084c-5da3-433b-9e92-9b1e44e07ed6
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4fb5084c-5da3-433b-9e92-9b1e44e07ed6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4fb5084c-5da3-433b-9e92-9b1e44e07ed6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4fb5084c-5da3-433b-9e92-9b1e44e07ed6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 92A49B51A49B36A7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root E6487B0D487ADC2D
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9be4ab3c-cb25-4993-bfa7-7662ff078c74 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 247.955326080 = 266.240004096  boot/grub/core.img                             1
 260.053791046 = 279.230631936  boot/grub/grub.cfg                             1
 228.243164062 = 245.074231296  boot/initrd.img-2.6.38-8-generic               2
 247.953594208 = 266.238144512  boot/vmlinuz-2.6.38-8-generic                  1
 228.243164062 = 245.074231296  initrd.img                                     2
 247.953594208 = 266.238144512  vmlinuz                                        1



```

---

### Post by Shervin Safavi on 2011-09-02
I have the same problem with my VAIO CW. can I use the same code to solve the problem?

---

