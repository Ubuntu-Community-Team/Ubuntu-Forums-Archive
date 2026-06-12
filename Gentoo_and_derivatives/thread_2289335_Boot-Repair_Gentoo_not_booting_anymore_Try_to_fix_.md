---
title: "Boot-Repair: Gentoo not booting anymore: Try to fix GRUB with Boot-Repair"
date: 2015-08-03
forum: Gentoo and derivatives
---

### Post by Johannes_Ebner on 2015-08-03
Dear All!

I have a big problem with my gentoo installation (on a HP MicroServer N40L): I had two hard disks (sda and sdb) with several Partitions:
sda1
sda2
sda3
sdb1
sdb2
sdb3

sda2 and sdb2 were used as SWAP (with PRIO Setting in fstap

sda1 and sdb1 were combined via mdadm to a Raid 1 and used as "/boot"
sda3 and sdb3 were combined via mdadm to a Raid 1 and used as "/"

Everyhting was working fine for a long time. Then I had to remove sdb and add a new sdb device (unfortunatley with unused windows installed). The system didnt boot anymore and showed "no boot meda found". 
I removed again sdb and tried to boot with sda only, same result.

I booted then with a gentoo boot cd and noticed that all files in "/" and also "/boot" are present, but when running mdstat I noticed, that the system said sda1 was a Raid0...
So I removed the software raid (mdadm --stop) from sda3 and sda1, changed the filesystem with cfdisk to "linux 82" and removed on both partitions the "superblock". Still not booting.

Then I tried to mount "/" and "/boot", chroot and installing grub again with "grub2-install /dev/sda" and "grub2-mkconfig". Both commnads were run successfully without any error message. 
But after reboot I only see the Grub Console "grub>".

Then I was running "Boot-Repair-Disk" it is running for 1 hour, but nothing happens. Does it take so long?

This is the output of "Boot-Repair-Disk". Any chance to boot the system without installing it new?

```

Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf /grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
                       This is .() 
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       385,559       385,497  83 Linux
/dev/sda2             385,560     8,385,929     8,000,370  82 Linux swap / Solaris
/dev/sda3           8,385,930 1,953,525,167 1,945,139,238  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        04b587b5-da16-4295-a2e1-740668df7686   ext2       
/dev/sda2        e9d0f8df-d93d-4111-876c-fccd218aa1f2   swap       
/dev/sda3        c84e6eb7-f91a-4c92-90c4-a34e3560bffc   ext3       
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       c08fc09f-9dfa-4563-950f-69300cddb08d   swap       
/dev/zram1       5af5ff7f-b144-4a9b-930f-65ef02248726   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Aug  3 10:01 ata-WDC_WD1003FBYX-01Y7B1_WD-WMAW30795967 -> ../../sda
lrwxrwxrwx 1 root root 10 Aug  3 09:59 ata-WDC_WD1003FBYX-01Y7B1_WD-WMAW30795967-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug  3 09:59 ata-WDC_WD1003FBYX-01Y7B1_WD-WMAW30795967-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug  3 09:59 ata-WDC_WD1003FBYX-01Y7B1_WD-WMAW30795967-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Aug  3 09:59 usb-MP_EMS_Virtual_CD_20090730-0:0 -> ../../sr0
lrwxrwxrwx 1 root root  9 Aug  3 09:59 usb-MP_EMS_Virtual_Floppy_20090730-0:2 -> ../../sdc
lrwxrwxrwx 1 root root  9 Aug  3 09:59 usb-MP_EMS_Virtual_HD_20090730-0:1 -> ../../sdb
lrwxrwxrwx 1 root root  9 Aug  3 10:01 wwn-0x50014ee206bda376 -> ../../sda
lrwxrwxrwx 1 root root 10 Aug  3 09:59 wwn-0x50014ee206bda376-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug  3 09:59 wwn-0x50014ee206bda376-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug  3 09:59 wwn-0x50014ee206bda376-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.conf: =============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub2-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3 --hint='hd0,msdos3'  c84e6eb7-f91a-4c92-90c4-a34e3560bffc
else
  search --no-floppy --fs-uuid --set=root c84e6eb7-f91a-4c92-90c4-a34e3560bffc
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ x$feature_timeout_style = xy ] ; then
  set timeout_style=menu
  set timeout=5
# Fallback normal timeout code in case the timeout_style feature is
# unavailable.
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Gentoo GNU/Linux' --class gentoo --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
    load_video
    if [ "x$grub_platform" = xefi ]; then
        set gfxpayload=keep
    fi
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  04b587b5-da16-4295-a2e1-740668df7686
    else
      search --no-floppy --fs-uuid --set=root 04b587b5-da16-4295-a2e1-740668df7686
    fi
    echo    'Loading Linux x86_64-4.0.5-gentoo ...'
    linux    /kernel-genkernel-x86_64-4.0.5-gentoo root=UUID=c84e6eb7-f91a-4c92-90c4-a34e3560bffc ro  
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-genkernel-x86_64-4.0.5-gentoo
}
submenu 'Advanced options for Gentoo GNU/Linux' $menuentry_id_option 'gnulinux-advanced-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
    menuentry 'Gentoo GNU/Linux, with Linux x86_64-4.0.5-gentoo' --class gentoo --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-x86_64-4.0.5-gentoo-advanced-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
        load_video
        if [ "x$grub_platform" = xefi ]; then
            set gfxpayload=keep
        fi
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  04b587b5-da16-4295-a2e1-740668df7686
        else
          search --no-floppy --fs-uuid --set=root 04b587b5-da16-4295-a2e1-740668df7686
        fi
        echo    'Loading Linux x86_64-4.0.5-gentoo ...'
        linux    /kernel-genkernel-x86_64-4.0.5-gentoo root=UUID=c84e6eb7-f91a-4c92-90c4-a34e3560bffc ro  
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-genkernel-x86_64-4.0.5-gentoo
    }
    menuentry 'Gentoo GNU/Linux, with Linux x86_64-4.0.5-gentoo (recovery mode)' --class gentoo --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-x86_64-4.0.5-gentoo-recovery-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
        load_video
        if [ "x$grub_platform" = xefi ]; then
            set gfxpayload=keep
        fi
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  04b587b5-da16-4295-a2e1-740668df7686
        else
          search --no-floppy --fs-uuid --set=root 04b587b5-da16-4295-a2e1-740668df7686
        fi
        echo    'Loading Linux x86_64-4.0.5-gentoo ...'
        linux    /kernel-genkernel-x86_64-4.0.5-gentoo root=UUID=c84e6eb7-f91a-4c92-90c4-a34e3560bffc ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-genkernel-x86_64-4.0.5-gentoo
    }
    menuentry 'Gentoo GNU/Linux, with Linux x86_64-3.18.12-gentoo' --class gentoo --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-x86_64-3.18.12-gentoo-advanced-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
        load_video
        if [ "x$grub_platform" = xefi ]; then
            set gfxpayload=keep
        fi
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  04b587b5-da16-4295-a2e1-740668df7686
        else
          search --no-floppy --fs-uuid --set=root 04b587b5-da16-4295-a2e1-740668df7686
        fi
        echo    'Loading Linux x86_64-3.18.12-gentoo ...'
        linux    /kernel-genkernel-x86_64-3.18.12-gentoo root=UUID=c84e6eb7-f91a-4c92-90c4-a34e3560bffc ro  
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-genkernel-x86_64-3.18.12-gentoo
    }
    menuentry 'Gentoo GNU/Linux, with Linux x86_64-3.18.12-gentoo (recovery mode)' --class gentoo --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-x86_64-3.18.12-gentoo-recovery-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
        load_video
        if [ "x$grub_platform" = xefi ]; then
            set gfxpayload=keep
        fi
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  04b587b5-da16-4295-a2e1-740668df7686
        else
          search --no-floppy --fs-uuid --set=root 04b587b5-da16-4295-a2e1-740668df7686
        fi
        echo    'Loading Linux x86_64-3.18.12-gentoo ...'
        linux    /kernel-genkernel-x86_64-3.18.12-gentoo root=UUID=c84e6eb7-f91a-4c92-90c4-a34e3560bffc ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-genkernel-x86_64-3.18.12-gentoo
    }
    menuentry 'Gentoo GNU/Linux, with Linux x86_64-3.18.11-gentoo' --class gentoo --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-x86_64-3.18.11-gentoo-advanced-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
        load_video
        if [ "x$grub_platform" = xefi ]; then
            set gfxpayload=keep
        fi
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  04b587b5-da16-4295-a2e1-740668df7686
        else
          search --no-floppy --fs-uuid --set=root 04b587b5-da16-4295-a2e1-740668df7686
        fi
        echo    'Loading Linux x86_64-3.18.11-gentoo ...'
        linux    /kernel-genkernel-x86_64-3.18.11-gentoo root=UUID=c84e6eb7-f91a-4c92-90c4-a34e3560bffc ro  
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-genkernel-x86_64-3.18.11-gentoo
    }
    menuentry 'Gentoo GNU/Linux, with Linux x86_64-3.18.11-gentoo (recovery mode)' --class gentoo --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-x86_64-3.18.11-gentoo-recovery-c84e6eb7-f91a-4c92-90c4-a34e3560bffc' {
        load_video
        if [ "x$grub_platform" = xefi ]; then
            set gfxpayload=keep
        fi
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  04b587b5-da16-4295-a2e1-740668df7686
        else
          search --no-floppy --fs-uuid --set=root 04b587b5-da16-4295-a2e1-740668df7686
        fi
        echo    'Loading Linux x86_64-3.18.11-gentoo ...'
        linux    /kernel-genkernel-x86_64-3.18.11-gentoo root=UUID=c84e6eb7-f91a-4c92-90c4-a34e3560bffc ro single 
        echo    'Loading initial ramdisk ...'
        initrd    /initramfs-genkernel-x86_64-3.18.11-gentoo
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't
# needed); notail increases performance of ReiserFS (at the expense of storage
# efficiency).  It's safe to drop the noatime options if you want and to
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>            <mountpoint>    <type>        <opts>        <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
#/dev/sda1        /boot        ext2        noauto,noatime    1 2
/dev/sda3        /        ext3        noatime        0 1
/dev/sda2        none        swap        sw,pri=1    0 0
/dev/sdb2        none        swap        sw,pri=1    0 0
#/dev/cdrom        /mnt/cdrom    auto        noauto,ro    0 0
#/dev/fd0        /mnt/floppy    auto        noauto        0 0

proc            /proc        proc        defaults    0 0
shm            /dev/shm    tmpfs        nodev,nosuid,noexec    0 0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/2848/mounts) leaked on lvs invocation. Parent PID 9296: bash
File descriptor 63 (pipe:[25814]) leaked on lvs invocation. Parent PID 9296: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-08-03__10h00 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2848/mounts) leaked on lvs invocation. Parent PID 4474: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- debian-installer/language=de keyboard-configuration/layoutcode?=de

=================== os-prober:
/dev/sda3:Gentoo Base System release 2.2:Gentoo:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="04b587b5-da16-4295-a2e1-740668df7686" TYPE="ext2"
/dev/sda2: UUID="e9d0f8df-d93d-4111-876c-fccd218aa1f2" TYPE="swap"
/dev/sda3: UUID="c84e6eb7-f91a-4c92-90c4-a34e3560bffc" SEC_TYPE="ext2" TYPE="ext3"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/zram0: UUID="c08fc09f-9dfa-4563-950f-69300cddb08d" TYPE="swap"
/dev/zram1: UUID="5af5ff7f-b144-4a9b-930f-65ef02248726" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

/mnt/boot-sav/sda1/grub/menu.lst detected

=================== sda3/etc/grub.d/ :
drwxr-xr-x   2 root    root     4096 Jul 19 10:00 grub.d
total 60
-rwxr-xr-x 1 root root  8684 Jul 19 10:00 00_header
-rwxr-xr-x 1 root root  9290 Jul 19 10:00 10_linux
-rwxr-xr-x 1 root root 10260 Jul 19 10:00 20_linux_xen
-rwxr-xr-x 1 root root 10862 Jul 19 10:00 30_os-prober
-rwxr-xr-x 1 root root   214 Jul 19 10:00 40_custom
-rwxr-xr-x 1 root root   216 Jul 19 10:00 41_custom
-rw-r--r-- 1 root root   483 Jul 19 10:00 README




=================== sda3/etc/default/grub :

# Copyright 1999-2015 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2
# $Header: /var/cvsroot/gentoo-x86/sys-boot/grub/files/grub.default-3,v 1.5 2015/03/25 01:58:00 floppym Exp $
#
# To populate all changes in this file you need to regenerate your
# grub configuration file afterwards:
#     'grub2-mkconfig -o /boot/grub/grub.cfg'
#
# See the grub info page for documentation on possible variables and
# their associated values.

GRUB_DISTRIBUTOR="Gentoo"

# Default menu entry
#GRUB_DEFAULT=0

# Boot the default entry this many seconds after the menu is displayed
#GRUB_TIMEOUT=5
#GRUB_TIMEOUT_STYLE=menu

# Append parameters to the linux kernel command line
#GRUB_CMDLINE_LINUX=""
#
# Examples:
#
# Boot with network interface renaming disabled
# GRUB_CMDLINE_LINUX="net.ifnames=0"
#
# Boot with systemd instead of sysvinit (openrc)
# GRUB_CMDLINE_LINUX="init=/usr/lib/systemd/systemd"

# Append parameters to the linux kernel command line for non-recovery entries
#GRUB_CMDLINE_LINUX_DEFAULT=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal.
# Note that you can use only modes which your graphic card supports via VBE.
# You can see them in real GRUB with the command `vbeinfo'.
#GRUB_GFXMODE=640x480

# Set to 'text' to force the Linux kernel to boot in normal text
# mode, 'keep' to preserve the graphics mode set using
# 'GRUB_GFXMODE', 'WIDTHxHEIGHT'['xDEPTH'] to set a particular
# graphics mode, or a sequence of these separated by commas or
# semicolons to try several modes in sequence.
#GRUB_GFXPAYLOAD_LINUX=

# Path to theme spec txt file.
# The starfield is by default provided with use truetype.
# NOTE: when enabling custom theme, ensure you have required font/etc.
#GRUB_THEME="/boot/grub/themes/starfield/theme.txt"

# Background image used on graphical terminal.
# Can be in various bitmap formats.
#GRUB_BACKGROUND="/boot/grub/mybackground.png"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to kernel
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY=true

# Uncomment to disable generation of the submenu and put all choices on
# the top-level menu.
# Besides the visual affect of no sub menu, this makes navigation of the
# menu easier for a user who can't see the screen.
#GRUB_DISABLE_SUBMENU=y

# Uncomment to play a tone when the main menu is displayed.
# This is useful, for example, to allow users who can't see the screen
# to know when they can make a choice on the menu.
#GRUB_INIT_TUNE="60 800 1"



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    maybesepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    no-grubenv    grub2,    no-docgrub,    grub2-mkconfig -o /boot/grub,    64,    no-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    grub2-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD1003FBYX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      32.3kB  197MB   197MB   primary  ext2            boot
2      197MB   4294MB  4096MB  primary  linux-swap(v1)
3      4294MB  1000GB  996GB   primary  ext3



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA WDC WD1003FBYX-0;
1:32.3kB:197MB:197MB:ext2::boot;
2:197MB:4294MB:4096MB:linux-swap(v1)::;
3:4294MB:1000GB:996GB:ext3::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type ext2 (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type ext3 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net watchdog zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G   14M  3.9G   1% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      799M  972K  798M   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  8.0K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G     0  3.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      ext2       183M   57M  117M  33% /mnt/boot-sav/sda1
/dev/sda3      ext3       913G  616G  252G  71% /mnt/boot-sav/sda3

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71a36929

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      385559      192748+  83  Linux
/dev/sda2          385560     8385929     4000185   82  Linux swap / Solaris
/dev/sda3         8385930  1953525167   972569619   83  Linux


Error: no package mgt for purge. Bitte melden Sie diese Nachricht an boot.repair@gmail.com
Error: no package mgt for purge. Bitte melden Sie diese Nachricht an boot.repair@gmail.com
Error: no package mgt for purge. Bitte melden Sie diese Nachricht an boot.repair@gmail.com
Error: no package mgt for purge. Bitte melden Sie diese Nachricht an boot.repair@gmail.com
Error: no package mgt for purge. Bitte melden Sie diese Nachricht an boot.repair@gmail.com
Error: no package mgt for purge. Bitte melden Sie diese Nachricht an boot.repair@gmail.com
Error: no package mgt for purge. Bitte melden Sie diese Nachricht an boot.repair@gmail.com


=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda3 into the MBR of sda, using the following options:     kernel-purge
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.

```

Br,
Johannes

---

### Post by Johannes_Ebner on 2015-08-03
Double Post: Please delete this Post!

---

### Post by Bucky Ball on 2015-08-03
We don't delete them, but yes, duplicate.

*Thread closed. *

---

### Post by oldfred on 2015-08-03
Moved to Gentoo sub-forum.
I do not know differences with Gentoo from Ubuntu.

But I might try fsck? This is Ubuntu version, not sure if same or not for you.
Run on both /boot & / partitions.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

