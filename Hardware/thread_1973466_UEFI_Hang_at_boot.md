---
title: "UEFI Hang at boot"
date: 2012-05-04
forum: Hardware
---

### Post by immerohnegott on 2012-05-04
I've just gotten a new Acer Aspire 5560 notebook, which has a UEFI firmware (Phoenix SecureCore Tiano, I think). Got Ubuntu installed (still working on getting Windows up in EFI mode). Boot menu shows an entry labeled "ubuntu" (assuming this is the nvram entry or whatever...still not that familiar with UEFI), loads GRUB and all that.

The issue is, it only loads the system half the time. Every other boot it just hangs after I hit enter at the GRUB menu. No HDD light, nothing. I'm not sure if this is an issue with GRUB-EFI, my system's firmware, or something else.

---

### Post by oldfred on 2012-05-05
UEFI is new.

How are you shutting down. Did you remember the elephants?

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

With BIOS grub if it knows you had an adnormal shutdown it presents menu so you can run repairs.

Post boot info script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by immerohnegott on 2012-05-05
haven't tried that magic key combo yet. didn't think to do so (only had to use it once in almost a decade...didn't really come to mind). I'll try that and post the results of bootinfoscript next time it fails booting into/shutting down from Ubuntu. I'm  installing some drivers in Win7 at the moment. It'll be a couple hours ;-)

Just to give you a better idea until then, dmesg doesn't show anything out of the ordinary. I don't even think the system is actually starting to boot when the hang occurs - it seems to drop as soon as I press enter in GRUB. The system is set up correctly for this kind of dual-boot AFAIK - GUID parition table, EFI sys partition at the start of the drive (300mb). Both systems load, but only on the second attempt - Ubuntu freezes right out of GRUB and Win7 right after the "Starting Windows" screen comes up.

---

### Post by immerohnegott on 2012-05-05
Still havent attempted key-sorcery during the freeze, but here's the results of bootinfoscript:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 EFI System partition
/dev/sda2         616,448       878,591       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         878,592   555,053,055   554,174,464 Data partition (Windows/Linux)
/dev/sda4     555,053,056   966,533,119   411,480,064 Data partition (Windows/Linux)
/dev/sda5     966,533,120   976,773,119    10,240,000 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4326-E07D                              vfat       
/dev/sda3        C4C6873AC6872C2C                       ntfs       
/dev/sda4        c8d398ea-15b5-4dbb-98e1-82926eaf0c69   ext4       
/dev/sda5        fb8a69a0-016a-4c08-9ffc-e7ae155fb6bb   swap       
/dev/sr0                                                iso9660    EFI partition backup

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/EFI partition backup iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt4)'
search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt4)'
  search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=c8d398ea-15b5-4dbb-98e1-82926eaf0c69 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=c8d398ea-15b5-4dbb-98e1-82926eaf0c69 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=c8d398ea-15b5-4dbb-98e1-82926eaf0c69 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=c8d398ea-15b5-4dbb-98e1-82926eaf0c69 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set=root c8d398ea-15b5-4dbb-98e1-82926eaf0c69
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
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=c8d398ea-15b5-4dbb-98e1-82926eaf0c69 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=4326-E07D  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda5 during installation
UUID=fb8a69a0-016a-4c08-9ffc-e7ae155fb6bb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 366.839702606 = 393.891131392  boot/grub/grub.cfg                             1
 265.675315857 = 285.266698240  boot/initrd.img-3.2.0-23-generic               1
 266.706699371 = 286.374137856  boot/initrd.img-3.2.0-24-generic               2
 384.803451538 = 413.179559936  boot/vmlinuz-3.2.0-23-generic                  1
 266.405017853 = 286.050209792  boot/vmlinuz-3.2.0-24-generic                  1
 266.706699371 = 286.374137856  initrd.img                                     2
 265.675315857 = 285.266698240  initrd.img.old                                 1
 266.405017853 = 286.050209792  vmlinuz                                        1
 384.803451538 = 413.179559936  vmlinuz.old                                    1


```

---

### Post by oldfred on 2012-05-05
Your recovery has the nomodeset line, does it let you boot to command line or then load whichever gui you have?

Does Windows boot ok, script did not mount sda2 which looks like it must be the Windows boot partition.

---

### Post by immerohnegott on 2012-05-05
I get full GUI in both systems. Everything functions once the system manages to load. I'm not sure if the issue is with the firmware not properly handling UEFI-enabled OS, or the UEFI-enabled OS aren't as UEFI-enabled as they should be.

---

### Post by oldfred on 2012-05-05
You can look in the log files with log file viewer and see if it is posting some error message, long time between tasks,  or trying to load & reload & failing on some driver sometimes.

Some have has to slow booting.

[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---

### Post by immerohnegott on 2012-05-05
I just had a brainwave. Renaming the efi directory on the usb install media forces the Ubuntu installer to run in BIOS emulation (brings up syslinux purple thing instead of the UEFI grub menu), which theoretically would allow me to install the OS without using GRUB-EFI, and therefore boot both systems from MBR instead of the EFI partition. Since the preinstalled (BIOS/MBR) Windows 7 worked normally with no hangs, would this approach work? Or would the prober still see the EFI and install that version of GRUB?

---

### Post by oldfred on 2012-05-05
If Windows is in efi mode no, but if in BIOS mode you should not be installing Ubuntu in efi mode.

How is drive partitioned gpt or MBR(msdos)?
Windows only boots in UEFI mode with gpt drives. 
Ubuntu will boot UEFI or BIOS from gpt or boot BIOS from MBR.

---

### Post by immerohnegott on 2012-05-05
Like I said earlier, the drive is CURRENTLY partitioned using GPT. I have both systems installed in EFI.

Originally, the system was running on MBR, with Windows operating under BIOS. I went the full EFI route out of ignorance, as I'm pretty new to the technology and there isn't any way to force BIOS mode in the system setup. The Ubuntu installer kept running in EFI, and I didn't know how to change that.

It would seem since I can now get the Ubuntu installer to run in BIOS mode, I should be safe to clean the disk and convert it back to MBR. I will try this and report findings. Having these hangs all the time is not a preferable way to run my system.

---

### Post by oldfred on 2012-05-06
You can convert.

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

But then I am not sure how to repair Windows. Whether Windows repairs would fix it or not is a question. Do you have a Windows repair CD or USB or full DVD that can run repairs?

I would leave efi & bios_grub partitions on the drives. I find booting Ubuntu from gpt drive with a small 1MB bios_grub partition and Windows XP on a MBR works. If you may want to convert back to UEFI someday, I would leave the efi partition, just remove boot flag in gparted or in gdisk change from boot ef00 to data type 8300.

---

### Post by immerohnegott on 2012-05-06
I just wiped the disk, reset to MBR and clean-installed both systems for BIOS mode. Both boot fine from GRUB in MBR. 

Stick a fork in it, it's done.

---

### Post by oldfred on 2012-05-06
Hey, whatever works.:)

---

### Post by Akita on 2012-05-22
Just to add some info for people wanting to play with UEFI. I've seen the same problem here with another Acer (Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows. I'd sure like to play with this UEFI thing, but it looks like not all of the vendors are up to speed with it yet.

---

