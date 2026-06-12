---
title: "Booting from secondary hard drive."
date: 2011-10-22
forum: Hardware
---

### Post by Broojo02 on 2011-10-22
Hi guys,
I installed the most recent version of Ubuntu recently on my old laptop because it had two 250GB hard drives, the C drive where the OS and all my data was stored and another D drive which I had barely used (contains 1 picture to keep it happy).

So I figured it would be good to make use of this empty D drive and install Ubuntu on it. I did it via a live USB. It seemed to go pretty well with no problems along the way but when it asked me to reboot my computer it wouldnt show me the GRUB menu and simply booted into windows.

From poking around on various forums I have gleaned that this is because the GRUB file is stored on the D drive and when the laptop boots it only looks at the C drive.

Is there any way I can copy over the GRUB files to my C drive properly, I have heard of problems with not all OSs being shown and stuff, my laptop uses Windows Vista (its old I promise) 32 bit. 

If theres any info you need to know please ask me.

---

### Post by Broojo02 on 2011-10-22
Minor bump from page 4, I would love to use this OS I have installed :P

---

### Post by drs305 on 2011-10-22
You can boot a LiveCD or USB to a Desktop. Mount your Ubuntu partition with the first command and install Grub to the MBR of sda with the second command. Note that this will overwrite the Windows information in the MBR and you will have to boot Windows via the Grub bootloader:

You will need to change XY to your Ubuntu partition, such as sdb1 or sdb5.
```

sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sdb5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
```
Don't include the partition number in the second command.


If you aren't sure of this information, please download/run the Boot Info Script and post the contents of RESULTS.txt 

You can get to the script's downlink page via the "BIS" link in my signature line.

After you reboot without the USB, if you didn't see the grub menu or Windows wasn't included in the menu, run:
```
sudo update-grub
```

---

### Post by Broojo02 on 2011-10-22
Thanks for the response, just wondering which partition I should mount, I have quite a few on my second HDD, here is the list using fdisk -l

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70253467

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   457682399   228841168+   7  HPFS/NTFS/exFAT
/dev/sda2       457682944   488394751    15355904    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6819befb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      503807      250880   83  Linux
/dev/sdb2          505854   488396799   243945473    5  Extended
/dev/sdb5          505856     4409343     1951744   82  Linux swap / Solaris
/dev/sdb6         4411392    23941119     9764864   83  Linux
/dev/sdb7        23943168   488396799   232226816   83  Linux

Disk /dev/sdc: 4003 MB, 4003463168 bytes
84 heads, 19 sectors/track, 4899 cylinders, total 7819264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ae3260f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064     7819263     3905600    c  W95 FAT32 (LBA)


```And here are the results of the script:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 2868576 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   457,682,399   457,682,337   7 NTFS / exFAT / HPFS
/dev/sda2         457,682,944   488,394,751    30,711,808   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       503,807       501,760  83 Linux
/dev/sdb2             505,854   488,396,799   487,890,946   5 Extended
/dev/sdb5             505,856     4,409,343     3,903,488  82 Linux swap / Solaris
/dev/sdb6           4,411,392    23,941,119    19,529,728  83 Linux
/dev/sdb7          23,943,168   488,396,799   464,453,632  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4003 MB, 4003463168 bytes
84 heads, 19 sectors/track, 4899 cylinders, total 7819264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064     7,819,263     7,811,200   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B444A5E444A5AA16                       ntfs       OS
/dev/sda2        A47CB5DD7CB5AB06                       ntfs       HP_RECOVERY
/dev/sdb1        f8d61951-a149-47d4-b252-b08b392c938c   ext2       
/dev/sdb5        67ee7433-c119-4154-996e-5cdb12b71943   swap       
/dev/sdb6        e7f47ac3-b665-469a-a8a5-479544de2253   ext4       
/dev/sdb7        52b7b863-03a9-4bfc-af3c-5e978a7d710a   ext4       
/dev/sdc1        885A-BBA0                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

============================= sdb1/grub/grub.cfg: ==============================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root e7f47ac3-b665-469a-a8a5-479544de2253
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux    /vmlinuz-3.0.0-12-generic-pae root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /vmlinuz-3.0.0-12-generic-pae root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux    /vmlinuz-3.0.0-12-generic root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root B444A5E444A5AA16
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root A47CB5DD7CB5AB06
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             2
               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                   55
               =                initrd.img-3.0.0-12-generic-pae               72
               =                vmlinuz-3.0.0-12-generic                      20
               =                vmlinuz-3.0.0-12-generic-pae                  20

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=e7f47ac3-b665-469a-a8a5-479544de2253 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=f8d61951-a149-47d4-b252-b08b392c938c /boot           ext2    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=52b7b863-03a9-4bfc-af3c-5e978a7d710a /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=67ee7433-c119-4154-996e-5cdb12b71943 none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

I tired sdb5 but it said /dev/sdb5 looks like swapspace - not mounted
mount: you must specify the filesystem type

---

### Post by drs305 on 2011-10-22
You have a separate /boot partition (sdb1) and your Ubuntu / parittion (sdb6).

In this case, you mount them both, then install grub:

```
sudo mount /dev/sdb6 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

Also, once you get Ubuntu booting successfully...
After booting into Windows, if it boots, you should remove /boot/**grub/**core.img from the Windows partition. This is a grub folder and file unrelated to Windows and it could confuse Windows since it has its own /boot/bcd folder.

---

### Post by Broojo02 on 2011-10-22
Thanks very much drs305, I followed the instructions, all seemed to go well for the time being although I got this message:

```

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.


```

I will restart and see if I get any further.

---

### Post by drs305 on 2011-10-22
There are certain utilities, Dell DataSafe and FlexNet among them, which write to a portion of the MBR (or just beyond it on the drive) normally used by bootloaders. There are lots of Internet posts of these utilities causing boot issues.

This caused problems for Grub, as well as other bootloaders, but the Grub developers have now worked around the issue and I don't think this is going to affect your boot.

---

### Post by Broojo02 on 2011-10-22
Ok cool, posting this from Vista atm, GRUB works perfectly, thanks very much for your help :)

---

### Post by drs305 on 2011-10-22
:P

Glad Windows is booting as well. Just remove the /boot/grub folder and the file within it on the Windows partition. Don't delete the /boot folder itself, which contains bcd.

If you don't have any other issues, please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post. It lets the helpers concentrate on unresolved problems.

Happy Ubuntu-ing !

---

### Post by Broojo02 on 2011-10-22
You are gonna hate me but I have a plethora of problems, seems I got a little carried away with Vista being able to boot.

When I tried booting ubuntu it got stuck at the checking battery part (white text on a black screen), now this is understandable because the battery in my laptop doesnt work (like I said its old :P) I have the power cable constantly plugged in.

So all I could do was press the power button and turn off the laptop, upon rebooting the text now stops at "Stopping Userspace bootsplash", I suppose all I can do is turn it off again?

Crumbs I can't think of where to start fixing this :/

---

### Post by drs305 on 2011-10-22
The 'checking battery state' may not be what it seems (although it could be). That message is often the last thing seen on the screen for a variety of problems.

Reboot and see if it happens again. Were you ever able to successfully boot Ubuntu after reinstalling Grub? Can you select the Recovery mode - you could try running the 'repair' option from the Recovery mode.

---

### Post by Broojo02 on 2011-10-22
I rebooted and it hung on another message so I rebooted again and it hung on the bootsplash part.

The options I have in recovery mode are resume, fsck, remount and root, which should I run?

Thanks for the responses.

---

### Post by drs305 on 2011-10-22
> **Broojo02 said:**
> I rebooted and it hung on another message so I rebooted again and it hung on the bootsplash part.

The options I have in recovery mode are resume, fsck, remount and root, which should I run?

Thanks for the responses.

If it hangs on the bootsplash, try rebooting. Press 'e' to edit the menu entry. Cursor to the end of the 'linux' line. Remove 'quiet splash' and add 'nomodeset'. You aren't having the 'classic' video driver problem, but it's something to try if the video isn't working normally. After typing the changes, CTRL-x to boot.

It sounds to me as if Grub is working but the boot is failing for some other reason. 

On older computers sometimes it's a 137GB BIOS limitation, but since you have a separate /boot partition this should not be the problem.

If it still isn't booting, please rerun the boot info script from the LiveCD/USB.

---

### Post by Broojo02 on 2011-10-22
I changed it to nomodeset and other than changing the font slightly :P it still hangs at checking battery which seems to be the most common hanging text.

Here are the results of the script:

Oh and the reason I havent deleted the windows vista boot files is because I couldnt find the boot folder.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 2868576 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   457,682,399   457,682,337   7 NTFS / exFAT / HPFS
/dev/sda2         457,682,944   488,394,751    30,711,808   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       503,807       501,760  83 Linux
/dev/sdb2             505,854   488,396,799   487,890,946   5 Extended
/dev/sdb5             505,856     4,409,343     3,903,488  82 Linux swap / Solaris
/dev/sdb6           4,411,392    23,941,119    19,529,728  83 Linux
/dev/sdb7          23,943,168   488,396,799   464,453,632  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4003 MB, 4003463168 bytes
84 heads, 19 sectors/track, 4899 cylinders, total 7819264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064     7,819,263     7,811,200   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B444A5E444A5AA16                       ntfs       OS
/dev/sda2        A47CB5DD7CB5AB06                       ntfs       HP_RECOVERY
/dev/sdb1        f8d61951-a149-47d4-b252-b08b392c938c   ext2       
/dev/sdb5        67ee7433-c119-4154-996e-5cdb12b71943   swap       
/dev/sdb6        e7f47ac3-b665-469a-a8a5-479544de2253   ext4       
/dev/sdb7        52b7b863-03a9-4bfc-af3c-5e978a7d710a   ext4       
/dev/sdc1        885A-BBA0                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

============================= sdb1/grub/grub.cfg: ==============================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root e7f47ac3-b665-469a-a8a5-479544de2253
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux    /vmlinuz-3.0.0-12-generic-pae root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /vmlinuz-3.0.0-12-generic-pae root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux    /vmlinuz-3.0.0-12-generic root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=e7f47ac3-b665-469a-a8a5-479544de2253 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f8d61951-a149-47d4-b252-b08b392c938c
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root B444A5E444A5AA16
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root A47CB5DD7CB5AB06
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             2
               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                   55
               =                initrd.img-3.0.0-12-generic-pae               72
               =                vmlinuz-3.0.0-12-generic                      20
               =                vmlinuz-3.0.0-12-generic-pae                  20

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=e7f47ac3-b665-469a-a8a5-479544de2253 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=f8d61951-a149-47d4-b252-b08b392c938c /boot           ext2    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=52b7b863-03a9-4bfc-af3c-5e978a7d710a /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=67ee7433-c119-4154-996e-5cdb12b71943 none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by drs305 on 2011-10-22
It looks like your grub is still looking for core.img on sda1; this may or may not be happening. The boot script sometimes fails to report the correct drive.

Let's try booting from the grub command prompt. I will assume you have a normal Grub menu since you can boot to the Recovery mode (even if we never used its options).

At the Grub prompt, press 'c' to get to the Grub prompt. You should see "grub>" 

Type these commands. You can use TAB completion to set the kernel version (Type vml then tab and it should help complete the version; same with initrd...):

```
[B]set prefix=(hd1,1)/grub
set root=(hd1,1)
linux /vmlinuz-3.0.0-12-generic-pae root=/dev/sdb6 ro
initrd /initrd.img-3.0.0-12-generic-pae[/B]
boot
```
If it boots, run:
```
sudo grub-install /dev/sda
sudo update-grub
```

**Correction:** Since you have a separate /boot, see bold line.

---

### Post by Broojo02 on 2011-10-22
On the third line it says error: file not found.

---

### Post by drs305 on 2011-10-22
Try the above commands again. Also, for some reason I was under the impression you couldn't change the BIOS boot order. If you can't manually boot with the commands above, and you *can* change the boot order, set the BIOS to boot your sdb drive first and see if it will read the correct core.img.

---

### Post by drs305 on 2011-10-23
Summary:
The Ubuntu system had a /, /boot and /home on the sdb drive. Initial attempts were to update the core.img, since there was one installed in the Windows partition on sda1. Grub was installed to the sda MBR.

Even after doing this via the LiveCD the system would hang during boot. Booting to the Recovery mode, dropping to a root shell with networking, we purged and reinstalled the nvidia drivers (nvidia-current) and resumed the boot from the Recovery mode. The system then booted. Grub was installed to the sda MBR and updated just to make sure.

After Ubuntu booted, the Windows partition was displayed in Nautilus and the OP found the /boot/grub folder and deleted it.

---

