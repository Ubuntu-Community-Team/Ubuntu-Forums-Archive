---
title: "caught in bios - endless loop on boot"
date: 2012-01-22
forum: Hardware
---

### Post by duckling9 on 2012-01-22
Hello
I have a Samsung netbook NF210 running Win7 and Ubuntu. It has been  running successfully for some months. I installed the Ubuntu after and  alongside the Win7. I recently rebooted into Windows and the Samsung  recovery solution started. I didn't know how this would treat my linux  partitions so I cancelled that. 

Since then the machine is on a startup loop: Samsung splash -> screen  with blinking cursor -> black screen -> repeat. Yuck. (I can access F2, which give me BIOS settings; but not F4, which allegedly starts the "Samsung Recovery Solution")

The machine doesn't come with Win7 install discs, and I didn't make a  recovery one. I have tried using the ones provided by neosmart, but they  don't seem to be helping yet.
I have run a ubuntu live from usb stick.

I have found others who have experienced a similar problem , but I can't  find any definitive answers, or ones that I can follow (for example my  Win7 repair USB doesn't work). Here's some examples:  [http://ubuntuforums.org/showthread.php?t=1858656](http://ubuntuforums.org/showthread.php?t=1858656) and
[http://www.linuxquestions.org/questi...etbook-864939/]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/problem-with-grub-win7-srs4-recovery-partition-samsung-n110-netbook-864939/")

I don't really understand boot processes/grub -- to the extent I don't  even understand where the grub is, and what starts it.. so look at Boot-Repair with trepidation, as I don't know what to click. I am happy to ferret about but don't know where to  begin to get a dual system functioning again (unfortunately i do need  both OS).

Your help would be very much appreciated!
dee

---

### Post by kleeh777 on 2012-01-22
Try a live disk with Parted Magic. 

Sometimes the "boot-flag" is somehow unflagged. Choose ur boot-partition (usually 100-500mb), right-click and chose Mangage Flags and set it to boot.

That helped me once.

Worth a try.

---

### Post by duckling9 on 2012-01-23
The first partition has boot flag set, so that seems ok (??) but i wondered if recovery partion should have this also set? As I said, I'm not really that clued up on this, though I have been googling extensively. 

Below is output of boot_info_script, which may or may not be ok... i can't see anything amiss? grateful for any suggestions!

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:   Syslinux looks at sector 1432800 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   107,161,599   106,954,752   7 NTFS / exFAT / HPFS
/dev/sda3         107,163,646   450,648,063   343,484,418   f W95 Extended (LBA)
/dev/sda5         107,163,648   420,483,710   313,320,063   7 NTFS / exFAT / HPFS
/dev/sda6         420,485,120   448,573,439    28,088,320  83 Linux
/dev/sda7         448,575,488   450,648,063     2,072,576  82 Linux swap / Solaris
/dev/sda4         450,648,064   488,392,703    37,744,640  27 Hidden NTFS (Recovery Environment)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7759 MB, 7759462400 bytes
94 heads, 46 sectors/track, 3504 cylinders, total 15155200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          3,184    15,155,199    15,152,016   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       313c16ec-df07-4271-92ce-7f753c07e15f   ext3       
/dev/sda1        4A105C8D105C81BD                       ntfs       SYSTEM
/dev/sda2        ACE4D45BE4D4297A                       ntfs       
/dev/sda4        2CCED2F8CED2B8F2                       ntfs       SAMSUNG_REC
/dev/sda5        EA12F44412F41773                       ntfs       
/dev/sda6        822578f9-bdf0-4324-aa57-c2e8a2595424   ext4       
/dev/sdb1        3852-D501                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=822578f9-bdf0-4324-aa57-c2e8a2595424 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=822578f9-bdf0-4324-aa57-c2e8a2595424 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=822578f9-bdf0-4324-aa57-c2e8a2595424 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=822578f9-bdf0-4324-aa57-c2e8a2595424 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=822578f9-bdf0-4324-aa57-c2e8a2595424 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=822578f9-bdf0-4324-aa57-c2e8a2595424 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 822578f9-bdf0-4324-aa57-c2e8a2595424
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4A105C8D105C81BD
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 2CCED2F8CED2B8F2
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
UUID=2CCED2F8CED2B8F2 /media/windows ntfs-3g defaults 0 0
UUID=EA12F44412F41773 /media/data ntfs-3g defaults 0 0
UUID=822578f9-bdf0-4324-aa57-c2e8a2595424 / ext4 defaults 0 1
--------------------------------------------------------------------------------

====================== sda6/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 211.721008301 = 227.333701632  boot/grub/core.img                             1
 211.704528809 = 227.316006912  boot/grub/grub.cfg                             1
 213.329589844 = 229.060902912  boot/initrd.img-2.6.38-12-generic             84
 203.888267517 = 218.923360256  boot/initrd.img-3.0.0-13-generic               2
 203.890800476 = 218.926080000  boot/initrd.img-3.0.0-14-generic               2
 207.572753906 = 222.879547392  boot/vmlinuz-2.6.38-12-generic                 5
 202.952556610 = 217.918648320  boot/vmlinuz-3.0.0-13-generic                  1
 202.999431610 = 217.968979968  boot/vmlinuz-3.0.0-14-generic                  1
 202.999431610 = 217.968979968  vmlinuz                                        1
 202.952556610 = 217.918648320  vmlinuz.old                                    1

================= sda6: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 209.117160797 = 224.537841664  boot/extlinux/chain.c32                        1
 202.631896973 = 217.574342656  boot/extlinux/extlinux.conf                    1

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by kleeh777 on 2012-01-23
u can only set one boot-flag pr harddisk

but it seems like u  did the partitioning urself? thought the boot partition was for the ubuntu

try and set the boot-flag at the sda6, that should get u into grub

---

### Post by oldfred on 2012-01-23
This is mostly about windows dual booting, but shows how all BIOS/MBR computers boot. You just need to look at pictures unless you want a lot of detail.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

The important parts of grub for booting are the code in the MBR and the grub.cfg file plus core.img which is hidden just after the MBR on most systems.  The others are for changing configuration.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Your bootinfo script results look ok. I thought the start of the recovery might have totally destroyed system as it is just an image of the drive as purchased and would totally rewrite the drive. So script is not seeing major issues.

Have you tried just reinstalling grub2's boot loader to the MBR. And or reinstalling the Windows boot loader and see if Windows will boot on its own? Windows repairCD should let your write a Windows boot loader to the MBR. But to boot Ubuntu you will need the liveCd/USB to reinstall grub or use Boot-Repair.

Boot flag only is used by Windows on the boot partitions which for you is sda1. Grub does not use a boot flag to know where to boot from. But a few BIOS do need a boot flag on a primary partition, just to let booting start (assumes Windows?).

---

### Post by duckling9 on 2012-01-23
oldfred - Thanks for the fantastically informative links. I am trying to digest- - I think by the end of this process i will have a much better understanding of this! :)
I cannot use the windows repair disk (I didn't make one and the one from neosmart doesn't seem to do anything useful)
However I do have a live ubuntu distro on usb (on which i am working here!) 

So, do I understand that the boot flag should be set to the partition with the IPL? Or should it be set for the 'first' PBR? And how do i know where this should be? Ie is ther any mileage with me trying to set the boot flag on sda6, my linux partition, as kleef777 suggests above?

---

### Post by oldfred on 2012-01-23
Grub does not use boot flag. Windows will only boot from a primary partition or sda1 thru sda4. The only reason to put a boot flag on a logical partition would be if you boot from and used lilo code in the PBR. Lilo works like Windows in that the MBR just looks for a PBR to boot to, but Windows only looks for primary partitions. We can use the Lilo boot loader in the MBR to boot the  Windows PBR or grub to chainload to the Windows PBR.

From boot script you can see Windows boot files.
Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Windows will only repair, boot from or install to the active partition which in Linux is the boot flag.

I have used the neosmart Windows 7 repairCd to create a USB repair and used it to run chkdsk on my XP install. It created a Windows 7 PBR and it still booted Windows XP (not sure why?), but I reinstalled from the Windows 7 repair USB a XP PBR.

---

