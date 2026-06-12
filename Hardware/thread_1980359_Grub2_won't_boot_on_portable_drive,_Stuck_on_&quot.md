---
title: "Grub2 won't boot on portable drive, Stuck on &quot;grub loading.&quot;"
date: 2012-05-15
forum: Hardware
---

### Post by unhnh on 2012-05-15
Hi everyone. I have a ubuntu 12.04 installed on my portble drive (1TB) in the 3rd partition, the partition format is ext4. But I have trouble booting on my HP dv6 6029tx laptop,after selecting the boot device from bios menu, it hangs on a black screen and nothing else, I guess it has stuck on stage 1?

if I press shift, then there is just a single line shows 
"grub loading." 

as in the img below. 
[IMG]https://lh6.googleusercontent.com/-zxeKHhPKYdU/T7HkTm-ugyI/AAAAAAAACxY/Lbwemg1MRwM/w326-h243-n-k/3.png[/IMG]


I've tried to reinstall grub2 and mbr, no luck. Is this a hardware issue? or related to compatibility?

interesting thing is my laptop had succeeded in booting previous version of ubuntu via USB drive, and the problem occurred after I reinstalled 12.04 on the portable drive with livecd.

---

### Post by wilee-nilee on 2012-05-15
Download this script exstract it to your dektop in a ubuntu setup, a  live  cd or install. Run the command with the external plugged in, and  post the  results.txt that will appear. Hit the # in the new reply window,  you will see code tags appear copy and paste that text in between.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by unhnh on 2012-05-15
> **wilee-nilee said:**
> Download this script exstract it to your dektop in a ubuntu setup, a  live  cd or install. Run the command with the external plugged in, and  post the  results.txt that will appear. Hit the # in the new reply window,  you will see code tags appear copy and paste that text in between.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

hi,wilee here is the result

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /123.BIN looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /123.BIN looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        /menu.lst /grldr /grub.exe /grldr /grldr.mbr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   194,996,223   194,789,376   7 NTFS / exFAT / HPFS
/dev/sda3         194,996,968 1,460,758,319 1,265,761,352   7 NTFS / exFAT / HPFS
/dev/sda4       1,460,758,320 1,465,144,064     4,385,745   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204883968 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    83,873,791    83,871,744   7 NTFS / exFAT / HPFS
/dev/sdb2          83,875,360 1,920,956,309 1,837,080,950   7 NTFS / exFAT / HPFS
/dev/sdb3       1,947,525,118 1,953,523,711     5,998,594   5 Extended
/dev/sdb5       1,947,525,120 1,953,523,711     5,998,592  82 Linux swap / Solaris
/dev/sdb4       1,920,956,416 1,947,523,071    26,566,656  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1030 MB, 1030225920 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2012160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63     2,012,159     2,012,097   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 12.04 LTS amd64
/dev/loop1                                              squashfs   
/dev/sda1        A4CC2B6BCC2B3748                       ntfs       &#31995;&#32479;&#20445;&#30041;
/dev/sda2        02CC2F28CC2F1587                       ntfs       
/dev/sda3        1A0AD1A80AD18165                       ntfs       &#20081;&#19971;&#20843;&#31967;
/dev/sda4        06B3-7773                              vfat       HP_TOOLS
/dev/sdb1        EE9EA2969EA256BD                       ntfs       Win8
/dev/sdb2        3E0273A9027364B5                       ntfs       Expansion Drive
/dev/sdb4        04f69aa1-ea63-4984-977b-908443a255c2   ext4       
/dev/sdb5        e5c8f7a3-342e-42fd-b7b1-c18cd0b6c877   swap       
/dev/sdc1        D6F4-921C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /isodevice               fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/Win8              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb4        /media/04f69aa1-ea63-4984-977b-908443a255c2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/D6F4-921C         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.lz                                      1
            ?? = ??             vmlinuz                                        1

=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos4)'
search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos4)'
  search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
  set locale_dir=($root)/boot/grub/locale
  set lang=zh_CN
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
menuentry 'Ubuntu&#65292;Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu&#65292;Linux 3.2.0-24-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    echo    '&#36733;&#20837; Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro recovery nomodeset 
    echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu&#65292;Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu&#65292;Linux 3.2.0-23-generic (&#24674;&#22797;&#27169;&#24335;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    echo    '&#36733;&#20837; Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro recovery nomodeset 
    echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F6CC0F08CC0EC33B
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 8 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root EE9EA2969EA256BD
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

=============================== sdb4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc4 during installation
UUID=04f69aa1-ea63-4984-977b-908443a255c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=e5c8f7a3-342e-42fd-b7b1-c18cd0b6c877 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

================================ sdc1/menu.lst: ================================

--------------------------------------------------------------------------------
# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title Windows 7 PE (ISO)
find --set-root /win7pe.iso
map /win7pe.iso (0xff) || map --mem /win7pe.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title  install ubuntu 12.04 64bit LTS
find --set-root /ubuntu-12.04-desktop-amd64.iso
map /ubuntu-12.04-desktop-amd64.iso (0xff) || map --mem /ubuntu-12.04-desktop-amd64.iso (0xff)
map --hook
kernel (0xff)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-12.04-desktop-amd64.iso
initrd (0xff)/casper/initrd.lz
boot
savedefault --wait=2

title android-x86 LiveCD 
root (hd0,0) 
kernel /android/kernel root=/dev/ram0 androidboot.hardware=eeepc  acpi_sleep=s3_bios,s3_mode SRC=/android
initrd /android/initrd.img
boot

title android-x86 LiveCD 2
root (hd0,0) 
kernel /android-2/kernel root=/dev/ram0 androidboot.hardware=asus  acpi_sleep=s3_bios,s3_mode SRC=/android-2
initrd /android-2/initrd.img
boot

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA
fallback 2
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)


\00--------------------------------------------------------------------------------

========================== sdc1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

========================= sdc1/grub.exe embedded menu: =========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by wilee-nilee on 2012-05-15
Actually I just noticed this, after writing the first post.

**sdb2: **__________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:    [B]  Grub2 (v1.97-1.98) in the file /123.BIN looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        [/B]

Boot a ubuntu live cd and open that partition and remove any grub file, and then reload grub to the mbr and try again

---

### Post by unhnh on 2012-05-15
> **wilee-nilee said:**
> Actually I just noticed this, after writing the first post.

**sdb2: **__________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:    [B]  Grub2 (v1.97-1.98) in the file /123.BIN looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        [/B]

Boot a ubuntu live cd and open that partition and remove any grub file, and then reload grub to the mbr and try again

OK, I tried boot a live cd and use chroot to log in to the system and reinstalled the mbr with sudo grub-install sdb, and reboot. 
and the problems remains... -_-# 

here is the new bootinfo

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /123.BIN looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        /menu.lst /grldr /grub.exe /grldr /grldr.mbr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   194,996,223   194,789,376   7 NTFS / exFAT / HPFS
/dev/sda3         194,996,968 1,460,758,319 1,265,761,352   7 NTFS / exFAT / HPFS
/dev/sda4       1,460,758,320 1,465,144,064     4,385,745   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204883968 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    83,873,791    83,871,744   7 NTFS / exFAT / HPFS
/dev/sdb2          83,875,360 1,920,956,309 1,837,080,950   7 NTFS / exFAT / HPFS
/dev/sdb3       1,947,525,118 1,953,523,711     5,998,594   5 Extended
/dev/sdb5       1,947,525,120 1,953,523,711     5,998,592  82 Linux swap / Solaris
/dev/sdb4       1,920,956,416 1,947,523,071    26,566,656  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1030 MB, 1030225920 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2012160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63     2,012,159     2,012,097   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 12.04 LTS amd64
/dev/loop1                                              squashfs   
/dev/sda1        A4CC2B6BCC2B3748                       ntfs       &#31995;&#32479;&#20445;&#30041;
/dev/sda2        02CC2F28CC2F1587                       ntfs       
/dev/sda3        1A0AD1A80AD18165                       ntfs       &#20081;&#19971;&#20843;&#31967;
/dev/sda4        06B3-7773                              vfat       HP_TOOLS
/dev/sdb1        EE9EA2969EA256BD                       ntfs       Win8
/dev/sdb2        3E0273A9027364B5                       ntfs       Expansion Drive
/dev/sdb4        04f69aa1-ea63-4984-977b-908443a255c2   ext4       
/dev/sdb5        e5c8f7a3-342e-42fd-b7b1-c18cd0b6c877   swap       
/dev/sdc1        D6F4-921C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /isodevice               fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/Win8              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb4        /media/04f69aa1-ea63-4984-977b-908443a255c2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/D6F4-921C         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos4)'
search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos4)'
  search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
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
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=04f69aa1-ea63-4984-977b-908443a255c2 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos4)'
    search --no-floppy --fs-uuid --set=root 04f69aa1-ea63-4984-977b-908443a255c2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root A4CC2B6BCC2B3748
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 02CC2F28CC2F1587
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

=============================== sdb4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc4 during installation
UUID=04f69aa1-ea63-4984-977b-908443a255c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=e5c8f7a3-342e-42fd-b7b1-c18cd0b6c877 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

================================ sdc1/menu.lst: ================================

--------------------------------------------------------------------------------
# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title Windows 7 PE (ISO)
find --set-root /win7pe.iso
map /win7pe.iso (0xff) || map --mem /win7pe.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title  install ubuntu 12.04 64bit LTS
find --set-root /ubuntu-12.04-desktop-amd64.iso
map /ubuntu-12.04-desktop-amd64.iso (0xff) || map --mem /ubuntu-12.04-desktop-amd64.iso (0xff)
map --hook
kernel (0xff)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-12.04-desktop-amd64.iso
initrd (0xff)/casper/initrd.lz
boot
savedefault --wait=2

title android-x86 LiveCD 
root (hd0,0) 
kernel /android/kernel root=/dev/ram0 androidboot.hardware=eeepc  acpi_sleep=s3_bios,s3_mode SRC=/android
initrd /android/initrd.img
boot

title android-x86 LiveCD 2
root (hd0,0) 
kernel /android-2/kernel root=/dev/ram0 androidboot.hardware=asus  acpi_sleep=s3_bios,s3_mode SRC=/android-2
initrd /android-2/initrd.img
boot

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA
fallback 2
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)


\00--------------------------------------------------------------------------------

========================== sdc1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

========================= sdc1/grub.exe embedded menu: =========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by wilee-nilee on 2012-05-15
Looks good now as far as I can tell, I wonder if the problem is that Ubuntu is at the end of the disc and grub is just having a hard time getting to it.

I assume you run a update-grub in the chroot and unmount it before rebooting.

There are other that are more experienced in this area than my self, they are daily forum members, and many more I suspect, I'm going to see what they have to say.

---

### Post by unhnh on 2012-05-15
> **wilee-nilee said:**
> Looks good now as far as I can tell, I wonder if the problem is that Ubuntu is at the end of the disc and grub is just having a hard time getting to it.

I assume you run a update-grub in the chroot and unmount it before rebooting.

There are other that are more experienced in this area than my self, they are daily forum members, and many more I suspect, I'm going to see what they have to say.

I didn't unmount the partition before rebooting, I'll try again and see if that would help. Also, I'm installing a ubuntu 12.04 on another 160G usb drive and it will be on the first partition, see if that would work.

I'll update the result after the installation. :pThanks for your help!!!

---

### Post by wilee-nilee on 2012-05-15
> **unhnh said:**
> I didn't unmount the partition before rebooting, I'll try again and see if that would help. Also, I'm installing a ubuntu 12.04 on another 160G usb drive and it will be on the first partition, see if that would work.

I'll update the result after the installation. :pThanks for your help!!!

You can unmount with a crtl-d in one fell swoop. :)

---

