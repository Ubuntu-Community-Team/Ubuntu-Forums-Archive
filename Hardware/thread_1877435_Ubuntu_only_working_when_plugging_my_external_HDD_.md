---
title: "Ubuntu only working when plugging my external HDD in."
date: 2011-11-08
forum: Hardware
---

### Post by Raglush on 2011-11-08
I'm a bit new on this forum (and with linux/ubuntu), so if I do anything wrong, please tell me. 

I installed ubuntu a couple of days ago, and enjoyed it, until I unplugged my external HDD and booted. Instead of a fine menu of OS options, I got a message saying: 

Error: no such device: XXXXX
Grub-rescue:

It seems that I can only boot up my computer with my external HDD plugged in. I didn't think that having my external harddrive plugged in while installing ubuntu would make any difference, but alas, it did. 

So now, can anyone help me with this?

---

### Post by diasf on 2011-11-08
did you install the linux on the external drive?

---

### Post by Raglush on 2011-11-08
> **diasf said:**
> did you install the linux on the external drive?

I just discovered that for some strange reason, I did. Even though I can't see it, I know it's there seems to missing 60 GB on the HDD.

Do I have to reinstall it all now?

---

### Post by coffeecat on 2011-11-08
You don't have to re-install. Some of the grub boot code is in /boot/grub in the root (or boot) partition.

Boot up Ubuntu with the external drive plugged in and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags. The easy way to add code tags is with the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar. The slightly more challenging way is by hand-typing BBCode - see the link in my sig.

With the information in your RESULTS.txt file we should be able to see how to get you booting independently of the hard drive, and to be able to boot Ubuntu from the external drive as well.

---

### Post by Raglush on 2011-11-08
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

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

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943279 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   885,020,671   884,609,024   7 NTFS / exFAT / HPFS
/dev/sda3         885,020,672   945,829,887    60,809,216   f W95 Extended (LBA)
/dev/sda5         885,022,720   945,829,887    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda4         945,829,888   976,773,167    30,943,280  12 Compaq diagnostics


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500105740288 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   859,169,600   859,167,553   7 NTFS / exFAT / HPFS
/dev/sdb2         859,170,814   976,766,975   117,596,162   5 Extended
/dev/sdb5         859,170,816   968,556,543   109,385,728  83 Linux
/dev/sdb6         968,558,592   976,766,975     8,208,384  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3C4A6B1D4A6AD2E6                       ntfs       
/dev/sda2        5E8A899C8A897177                       ntfs       
/dev/sda4        3CE4D25EE4D219CA                       ntfs       LENOVO_PART
/dev/sda5        C8040786040776AA                       ntfs       LENOVO
/dev/sdb1        F47A46D67A4694F0                       ntfs       Elements SD
/dev/sdb5        6a2444ad-620f-4414-ae66-4bfec11245c3   ext4       
/dev/sdb6        8d90d920-8618-4620-a357-ba1a292d936b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/Elements SD       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 6a2444ad-620f-4414-ae66-4bfec11245c3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 6a2444ad-620f-4414-ae66-4bfec11245c3
  set locale_dir=($root)/boot/grub/locale
  set lang=da_DK
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a2444ad-620f-4414-ae66-4bfec11245c3
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6a2444ad-620f-4414-ae66-4bfec11245c3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a2444ad-620f-4414-ae66-4bfec11245c3
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6a2444ad-620f-4414-ae66-4bfec11245c3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a2444ad-620f-4414-ae66-4bfec11245c3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a2444ad-620f-4414-ae66-4bfec11245c3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 3C4A6B1D4A6AD2E6
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 3CE4D25EE4D219CA
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=6a2444ad-620f-4414-ae66-4bfec11245c3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=8d90d920-8618-4620-a357-ba1a292d936b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```I hope I did this the right way. 
Btw, I'm not really interested in having ubuntu on my external HDD, but thanks anyway.

---

### Post by coffeecat on 2011-11-08
OK. If you don't want Ubuntu on the external drive, the quickest and simplest thing to do is to rewrite the Windows bootloader to the mbr of sda. That will allow you to boot straight into Windows.

You need a Windows 7 repair CD which you can prepare from inside Windows 7. If you have not done so already, here is how to do it:

[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

You need Windows to watch that - it needs Silverlight. :(

Once you've got the CD, boot up with it and choose command prompt. Now simply run "bootrec /FixMbr". For more, see here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Now you should be able to boot into Windows - no grub menu, no grub error.

If you want help installing Ubuntu in such a way that you do not need to have the external drive plugged in, just post back.

And good luck! :)

---

### Post by Raglush on 2011-11-09
YES! It worked! Now I don't have that menu, and I dont receive any grub errors.

Now, the ubuntu OS partition is still on the external HDD, how do I remove that? 
And I would love some help with installing ubuntu correctly :D

---

### Post by coffeecat on 2011-11-09
> **Raglush said:**
> And I would love some help with installing ubuntu correctly :D

You have two options. 

1 - Simply keep your present installation of Ubuntu on the external drive. You would need to install grub to the mbr of the sdb drive with the live Ubuntu CD and set the BIOS to boot from a USB drive if plugged in. The installation of grub is very easy and I can tell you how if you want. With this setup you would boot into Windows without the USB HD plugged in, and you would get the grub menu for both Ubuntu and Windows with the drive plugged in.

2 - Delete your sdb Ubuntu partitions as below and reinstall Ubuntu to sda - perhaps replacing sda5, depending on what is on sda5. If you want to do that, I suggest you mark this thread as solved and start a new one with a more relevant title. In your first post, post the Gparted screenshot I suggest you take below and post any details of your external drive and how you intend to use it, which may or may not be relevant.

> **Raglush said:**
> Now, the ubuntu OS partition is still on the external HDD, how do I remove that? 

You need to remove two logical partitions, sdb5 the Ubuntu root partition and sdb6 the swap partition. You may also want to remove the extended partition (sdb2) if you want just one large primary NTFS partition, or you may want to keep it for flexibility. In theory you might be able to remove the Linux partitions with the Windows Disk Management utility, but that gets a bit confused when confronted with logical partitions with Linux filesystems, so it would be safer to use Gparted from the live Ubuntu CD.

Boot up the live CD and choose "try Ubuntu". In the live desktop open Gparted. In the drop-down, top-right of the Gparted window, choose "/dev/sdb". Double-check you've got this right. You do not want to be removing partitions form sda! First, right-click on sdb6/swap and choose "swapoff" which will remove the lock from it and sdb2. Mark sdb6 and sdb5 for deletion and then click on the apply button - the green tick. If you want to remove the extended partition, mark and apply that as well.

While you are in Gparted you could create new partitions in sdb if you want. You can create NTFS partitions which will work just fine with Windows, but if you want to resize sdb1, this might be better done with the Windows Disk Management utility. I generally recommend using Windows DM for resizing a C: partition because in some instances Windows reacts badly to having its C: partition resized with a Linux partitioner. sdb1 looks to be a data partition, so you could use Gparted but I'm simply suggesting caution. 

And... while you have Gparted open, go back to sda in the drop-down at top-right and take a screenshot of the open window. Alt+PrintScr is the key combination. Save that for if you need to start a new thread (see above).

Another suggestion... You may or may not understand the distinction between primary, extended and logical partitions. Whether or not you do, it's a good idea to have a good grasp of the fundamentals of partitioning and of how to use Gparted before doing anything but a basic installation of Ubuntu. Here's a useful link:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Read through all the links there and you will be well-prepared for installing Ubuntu again. :)

---

### Post by Raglush on 2011-11-10
Thank you! It worked, and now I have the ubuntu/windows 7 setup I wanted.
Cheers

---

### Post by Ultra Cronic on 2011-11-23
> **Raglush said:**
> I just discovered that for some strange reason, I did. Even though I can't see it, I know it's there seems to missing 60 GB on the HDD.

Do I have to reinstall it all now?

I did the same thing but only on purpose rather then by accident, When I put the external usb SATA drive in the laptop main internal drive "C". 
I simply ran the setup disk and chose "Rescue Broken System" and got a tad nervous when the setup routine came up as though I was doing a fresh install, but don't panic, after typing in the time zone key board and VERY IMPORTANT when asked to creat a login name "Use The Same One" that you already have in their!!! or else:(!!
Then the setup will bounce you back to the options page and select install/update grub bootloader, now pay attention, if you have an internal drive that is a SATA type, the options give you instructions on what to type in the command line. In my case it was /dev/sba  THATS IT!!!
/dev/sba1 would either be a partition on the same drive or an internal slave. 
Now possessing a SCSI drive or an IDE drive may change all this. Know what your drive is inside before you do this, most newer machines use SATA, some people in the tech world call the IDE types PATA now, If you do not want to run a fresh setup and the internal drive is different from your external one Use AcronisII or Ghost to clone the internal drive from the external one then run the setup/Rescue a broken system option .
-------Or just run a pure scratch setup and grab your saved files from the external drive after loading up your extra programs. :confused:. There are ways around this it depends on your level of technical insanity.

---

