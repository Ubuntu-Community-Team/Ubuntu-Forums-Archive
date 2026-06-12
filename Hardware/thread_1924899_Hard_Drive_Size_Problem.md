---
title: "Hard Drive Size Problem"
date: 2012-02-13
forum: Hardware
---

### Post by darkeagle03 on 2012-02-13
My apologies if this has been asked before. I did a quick search both here and on Google but didn't find much.

I recently installed Ubuntu 11.10 on a new build (32-bit version #-o but it works fine after the pae install so I'll keep it for now). When I did the install I did a clean format of an old 150GB hard drive I had lying around. Everything worked great. I then transferred the OS to a 32 GB SSD drive to take advantage of the speed, noise, etc. I used GParted to format the SSD (ext4), reduce the primary partition of my 150GB to 10GB, and copy / paste the newly sized partition to my SSD. This created a 10GB partition on the SSD which I made bootable. After this was done I got rid of the 150GB (I have another drive for non-OS files) and booted up. It worked, so I ran GParted to increase the 10GB partition to the full 32GB of the drive. 

Everything's working perfectly, with one exception. Ubuntu still only recognizes 10GB on the SSD. The BIOS reads 32GB, and subsequent runs of GParted continue to show a single partition of 32GB, so it seems like the re-partition went through. But the OS refuses to recognize more than the 10GB. Of course, with that little space I'm running out of room very rapidly.


I'm a pretty proficient computer guy, but effectively a first-time Linux user. I'm loving what I see so far, but need to improve my expertise before I can handle some of these things purely on my own... Thanks for any help you can provide :)

---

### Post by oldfred on 2012-02-13
Did you do a image copy? Sometimes that resets a drive, but you say some tools show it correctly.

Post boot info script. It shows drives several ways. Use the git version as it has some fixes. 

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Instructions here:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by ajgreeny on 2012-02-13
Why not shrink the SSD to a 10GB partition for / and make a new partition ext4 as /home or /data.  It could make life a lot easier next time you want to do a clean install of the OS.

As for your actual question, I'm afraid I haven't got a clue.

PS:  Is ext4 the correct filesystem for an SSD disk?  I know, (at least I think I know), that ubuntu installed, for example, on a USB flash drive should be ext2.  Perhaps a proper SSD is different.

---

### Post by darkeagle03 on 2012-02-13
> **oldfred said:**
> Did you do a image copy? Sometimes that resets a drive, but you say some tools show it correctly.

Post boot info script. It shows drives several ways. Use the git version as it has some fixes. 

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Instructions here:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

I'll do this and post in a second. Thanks for the reply!

> **ajgreeny said:**
> Why not shrink the SSD to a 10GB partition for / and make a new partition ext4 as /home or /data.  It could make life a lot easier next time you want to do a clean install of the OS.

As for your actual question, I'm afraid I haven't got a clue.

PS:  Is ext4 the correct filesystem for an SSD disk?  I know, (at least I think I know), that ubuntu installed, for example, on a USB flash drive should be ext2.  Perhaps a proper SSD is different.

I suppose I could try setting it to 2 partitions. I really didn't think it would be a problem to just have a single partition though, and in my mind it was easier that way, so I just went for it.

Honestly, when I chose ext4 I had no clue. I chose it because it seemed like the latest Linux file system and I figured if I chose wrong at that early stage I could just reformat :). I have since looked it up a bit and saw some posts of people saying ext4 works fine for SSDs. Still, it is something to try if I can't find anything else. Regardless, I'd like to learn a little more about what's going on and how to debug / deal with these sorts of problems. I don't like not being independent or not knowing what's going on :)

---

### Post by darkeagle03 on 2012-02-13
oh, one other Q: I recently ran the backup utility (to Ubuntu One). Having not looked at it in much detail, I'm not certain entirely what it backs up. If I were to reformat my drive with a clean install, would it be easy to restore that backup and get back all my programs, tweaks, etc. that I've installed? I've already installed / modified a fair bit of stuff that I'd prefer to not re-install / setup manually if I can avoid it.

---

### Post by darkeagle03 on 2012-02-13
> **oldfred said:**
> Did you do a image copy? Sometimes that resets a drive, but you say some tools show it correctly.

Post boot info script. It shows drives several ways. Use the git version as it has some fixes. 

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```Instructions here:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 388273 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 32.0 GB, 32044482560 bytes
255 heads, 63 sectors/track, 3895 cylinders, total 62586880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    62,557,109    62,557,047  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,465,147,391 1,465,145,344  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1039 MB, 1039663104 bytes
256 heads, 32 sectors/track, 247 cylinders, total 2030592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32     2,030,591     2,030,560   4 FAT16 <32M


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        66218d7d-0b93-4d02-870a-54a142a03c4b   ext4       
/dev/sdb1        950a916c-914a-431f-a934-77d85b4bbddd   ext4       Storage
/dev/sdc1                                               vfat       LEXAR

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/LEXAR             vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /media/MYTH2             iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    echo    'Loading Linux 3.0.0-16-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-16-generic-pae root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    echo    'Loading Linux 3.0.0-15-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-15-generic-pae root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=66218d7d-0b93-4d02-870a-54a142a03c4b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 66218d7d-0b93-4d02-870a-54a142a03c4b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=66218d7d-0b93-4d02-870a-54a142a03c4b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=b68df177-7412-4744-ba1c-c10a2563b306 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   5.252021313 = 5.639314944    boot/grub/core.img                             1
   9.619983196 = 10.329378304   boot/grub/grub.cfg                             1
   0.631461620 = 0.678026752    boot/initrd.img-3.0.0-12-generic               2
   6.320815563 = 6.786924032    boot/initrd.img-3.0.0-15-generic               2
   6.655662060 = 7.146462720    boot/initrd.img-3.0.0-15-generic-pae           2
   9.728862286 = 10.446286336   boot/initrd.img-3.0.0-16-generic               2
   9.692798138 = 10.407562752   boot/initrd.img-3.0.0-16-generic-pae           2
   0.369304180 = 0.396537344    boot/vmlinuz-3.0.0-12-generic                 35
   3.907592297 = 4.195745280    boot/vmlinuz-3.0.0-15-generic                  1
   6.363868237 = 6.833151488    boot/vmlinuz-3.0.0-15-generic-pae              1
   9.316852093 = 10.003893760   boot/vmlinuz-3.0.0-16-generic                  1
   9.387305737 = 10.079542784   boot/vmlinuz-3.0.0-16-generic-pae              1
   9.692798138 = 10.407562752   initrd.img                                     2
   9.728862286 = 10.446286336   initrd.img.old                                 2
   9.387305737 = 10.079542784   vmlinuz                                        1
   9.316852093 = 10.003893760   vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# Created by generate-pxe-menu! Do NOT edit unless you know what you are doing! 
# Keep those comment "MENU DEFAULT" and "MENU HIDE"! Do NOT remove them.
# Note!!! If "serial" directive exists, it must be the first directive
default vesamenu.c32
timeout 300
prompt 0
noescape 1
MENU MARGIN 5
 MENU BACKGROUND Gsplash.png
# Set the color for unselected menu item and timout message
 MENU COLOR TITLE    1;36;44    #ffffffff #00000000
 MENU COLOR SEL      7;37;40    #FF000000 #FFC0C0C0
 MENU COLOR HOTSEL   1;7;37;40  #FF000000 #FFC0C0C0

# MENU MASTER PASSWD

say **********************************************************************
say GParted.
say Gnome Partition Editor.
say http://gparted.org
say THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK! 
say **********************************************************************

# Allow client to edit the parameters
ALLOWOPTIONS 1

# simple menu title
MENU TITLE http://gparted.org

# Since no network setting in the squashfs image, therefore if ip=frommedia, the network is disabled. That's what we want.
label GParted Live
  MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Default settings)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt  ip=frommedia  nosplash
  TEXT HELP
  * GParted live version: 0.11.0-10. Live version maintainer: Steven Shiau
  * Disclaimer: GParted live comes with ABSOLUTELY NO WARRANTY
  ENDTEXT

MENU BEGIN Other modes of GParted Live
label GParted Live (To RAM)
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (To RAM. Boot media can be removed later)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt  toram=filesystem.squashfs ip=frommedia  nosplash
  TEXT HELP
  All the programs will be copied to RAM, so you can
  remove boot media (CD or USB flash drive) later
  ENDTEXT

label GParted Live without framebuffer
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Safe graphic settings, vga=normal)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt ip=frommedia nomodeset vga=normal nosplash
  TEXT HELP
  Disable console frame buffer support
  ENDTEXT

label GParted Live failsafe mode
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Failsafe mode)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt acpi=off irqpoll noapic noapm nodma nomce nolapic nosmp ip=frommedia nomodeset vga=normal nosplash
  TEXT HELP
  acpi=off irqpoll noapic noapm nodma nomce nolapic 
  nosmp nomodeset vga=normal nosplash
  ENDTEXT

MENU END
label local
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL Local operating system in harddrive (if available)
  # MENU PASSWD
  # 2 method to boot local device:
  # (1) For localboot 0, it is decided by boot order in BIOS, so uncomment the follow 1 line if you want this method:
  # localboot 0

  # (2) For chain.c32, you can assign the boot device.
  # Ref: extlinux.doc from syslinux
  # Syntax: APPEND [hd|fd]<number> [<partition>]
  # [<partition>] is optional.
  # Ex:
  # Second partition (2) on the first hard disk (hd0);
  # Linux would *typically* call this /dev/hda2 or /dev/sda2, then it's "APPEND hd0 2"
  #
  kernel chain.c32
  append hd0
  TEXT HELP
  Boot local OS from first hard disk if it's available
  ENDTEXT


# Note! *.bin is specially purpose for syslinux, 
# Do NOT use memtest.bin, use memtest instead of memtest.bin
label memtest
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL Memory test using Memtest86+
  # MENU PASSWD
  kernel /live/memtest
  TEXT HELP
  Run memory test using Memtest86+
  ENDTEXT

--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by darkeagle03 on 2012-02-13
It looks to me like the 32 GB shows up in the results. Perhaps the error is between the seat and the CPU... What I've been seeing is in various / most programs it will say things like "space used: 7GB, space available: 3GB"

---

### Post by oldfred on 2012-02-13
I do not see anything wrong either.


Your partitioning does not look like it is optimized for SSD type drives.

Yours starts at sector 63 which is not divisible by 8.

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
$ sudo parted /dev/sda unit s print

Also if only booting Linux from an SSD, it may be better to use gpt partitioning. That will erase drive and you cannot use dd with gpt as internal structure are not to be copied.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

---

### Post by darkeagle03 on 2012-02-13
Thanks for the help, and sorry for the delay. Here's the results of the sudo parted command:

```

Model: ATA PATRIOT MEMORY 3 (scsi)
Disk /dev/sda: 62586880s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End        Size       Type     File system  Flags
 1      63s    62557109s  62557047s  primary  ext4         boot

```

Thanks for the links. They definitely make for some interested reading and I'll have to study them a bit more. I don't think much of my system is optimized right now, and I'll definitely want to go back and do what I can once I learn more. 

That said, I doubt any optimization will recover 70% of my hard drive... is there some way that I could just be lookng at something wrong and there really is about 30GB that's being used by something? Perhaps I'm using the wrong tools? Again, I am pretty much brand new to Linux

---

### Post by darkeagle03 on 2012-02-14
After a little bit of reading and poking I did find some interesting items. I unmounted everything other than my primary drive then ran df -TH. The results are below. 

```

Filesystem    Type     Size   Used  Avail Use% Mounted on
/dev/sda1     ext4      11G    11G   119M  99% /
udev      devtmpfs     4.2G    13k   4.2G   1% /dev
tmpfs        tmpfs     1.7G   934k   1.7G   1% /run
none         tmpfs     4.2G   418k   4.2G   1% /run/shm
/home/warren/.Private
          ecryptfs      11G    11G   119M  99% /home/warren

```You'll notice that when everything is added together it comes to about 32 GB. Now my questions are:
1) Why do none of the graphical programs show anything that adds to this total?
2) Is there a program I can get that shows me the contents of an entire drive in some kind of a graphical size breakdown properly?
3) What are udev, tmpfs, none, and /home/warren/.Private? (warren is my login)
4) Why do udev, tmpfs, and none have so much space allocated when practically nothing is being used?
5) Can I either eliminate or move these items w/out reinstalling or screwing up my system? If so, how?

---

### Post by oldfred on 2012-02-14
I do not know encryption, but wonder if that is part of the issue. I believe the .private is part of the encryption. All the tmpfs are temp files created by the system.

Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

### Post by darkeagle03 on 2012-02-14
It definitely looks like it is part of the issue. Do you know if there's any way to just turn encryption off? I have no real need for it. I only set it up because at the time of the install I had no reason not to and it sounded like a nice little security measure. I had no idea it was so costly and really don't need anything secured like that on this machine...

---

### Post by ThomasAndersn on 2012-02-15
hi, first u have to determine the size of ur drive, run the following command:
sudo lshw -C disk

If its shows ur drive size is 150 GB, then to create partition use Gparted, run the following command:
gksudo gparted

Now select ur SSD drive from the drop down list.
Right click on the whitebat and choose NEW.
For new size the number should be the maximum allowable, to fill the entire disk.
choose primary partition.
use "ext3" filesystem if u want to use the partition only in ubuntu , If u want to use it in windows choose "NTFS".
Now click on the Add.
Click Apply. Then the disk will be formatted & partitioned.

---

### Post by darkeagle03 on 2012-02-20
Resolution - in case anyone else has a similar issue and stumbles on this thread:

The problem had to do with the encrypted home directory. It effectively doubled the size of my home with half of that being in a hidden area that most GUI programs didn't detect. So home = 5GB, and encrypted home = another 5GB that isn't easily seen. 

I didn't really need the encryption in the first place, but I didn't find any good way of removing it from a quick search. I probably could have corrected the problem by moving the home area to the bigger hard drive but it all seemed more trouble than it was worth so I just reformatted the drive (btrfs this time thanks to oldfred) and re-installed Ubuntu 11.10 (64-bit this time). I turned off the encrypted home directory and moved home to the larger hard drive. 

Everything seems good now :) My only complaint is that the vast majority of my programs will be executed from the disk-based hard drive and not my SSD because that's where home resides. I wish it was easier to choose which physical disk / partition the program got installed on, like I could with Windows.

---

### Post by oldfred on 2012-02-20
Programs are not in /home just user settings & program data.

Even though the Phoronix comparison showed btrfs as very good, I thought ext4 held up well and is currently the 'standard', so I use ext4 for all new Linux partitions.

My new SSD had the entire system on the SSD including /home. But I split my /home and only have the hidden settings in /home. All data is in a data partition and linked back to /home. Even those programs that store data in hidden .folders get moved to my data partition if the data starts to become large. The only large hidden folder I have not moved is .wine as I understand that is more difficult.

---

