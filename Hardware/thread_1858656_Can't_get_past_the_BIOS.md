---
title: "Can't get past the BIOS"
date: 2011-10-12
forum: Hardware
---

### Post by tbarton on 2011-10-12
I have two OS's installed: Windows 7 and Ubuntu. In Windows 7, the brightness keys stopped working after I installed a service pack. I tried system recovery, but they still didn't work. I tried the "recovery" option I get when booting up, but that seemed to be to reinstall Windows. Please note the recovery tool seemed to be a Samsung tool, not a Windows tool (what I really wanted was to start in safe mode). Since I couldn't see an "exit" option, I had to just switch my computer off.

But that was the fatal blow. Not I can't get past the BIOS. My computer goes through an endless circle: Samsung loading page (with F2 option for BIOS and F4 for recovery), blank screen, restart, Samsung loading page...). Doesn't make any difference if I press F4.

I'm in the middle of downloading a Linux Live OS to try to boot from USB but I'm not convinced that will work, and even if it does, I'm not sure how I'll get the computer working properly again. Any suggestions? I'm not even convinced I'll be able to get into Linux Live.

---

### Post by sanderd17 on 2011-10-12
You should be able to boot a live CD or USB, and if that's booted, give us the output of the boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tbarton on 2011-10-12
OK, I've managed to get somewhere. Spent ages creating an ISO from my Linux Live CD, but it was very old [noparse](Ubuntu 8)[/noparse], and that edition is not on the list of distributions on the USB installer. I then tried with TinyCore (downloading is slow tonight so I went for a small distribution), and it started booting from my USB, but then I got this error message: "Could not find kerne image /boot/vmlinuz"

I'm about to try with a LuPu (Puppy) distribution. If this doesn't work, I'll set Ubuntu off downloading overnight and try with that. Hope I can get this sorted.

Tim

---

### Post by tbarton on 2011-10-12
I hope this ok for you. I tried the commands in the terminal, and I kept get a message saying no such file or folder existed (even though I'm convinced I was typing it correctly. Anyway, clicking on the *.sh file produced a results file, which hopefully is good enough.

It's reassuring to know I can at least boot into something. I just hope I can recover my existing operating systems without a complete reinstall. Maybe I could reinstall the bios from within the Linux Live installation?

It's way past bed time, so I won't be on here again for a several hours, but hopefully I'll have some nice answers from people across the pond while I'm sleeping. Thanks for the help you've already given.

I'm going to download Ubuntu overnight anyway, as I'm much more familiar with that system and will probably find it easier to do anything I need to do from there

Tim

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

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
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   115,550,207   115,343,360   7 NTFS / exFAT / HPFS
/dev/sda3         115,552,254   283,604,991   168,052,738   f W95 Extended (LBA)
/dev/sda5         115,552,256   200,054,694    84,502,439   7 NTFS / exFAT / HPFS
/dev/sda6         200,054,784   279,431,167    79,376,384  83 Linux
/dev/sda7         279,433,216   283,604,991     4,171,776  82 Linux swap / Solaris
/dev/sda4         283,604,992   312,578,047    28,973,056  27 Hidden NTFS (Recovery Environment)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5C92D60492D5E316                       ntfs       SYSTEM
/dev/sda2        7654372A5436ED0D                       ntfs       
/dev/sda4        764C4A4E4C4A0977                       ntfs       SAMSUNG_REC
/dev/sda5        5C869D5C869D380A                       ntfs       
/dev/sda6        9c669019-ee54-4adb-9af4-9a0d3a103449   ext4       
/dev/sda7        ae65b526-5325-472f-950b-e9d8fba89374   swap       
/dev/sdb1        09E4-264A                              vfat       PENDRIVE
/dev/sdc1        F46B-58A2                              vfat       CLAUER

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)
/dev/sda1        /mnt/sda1                fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,blksize=4096)
/dev/sda2        /mnt/sda2                ntfs       (ro,relatime,uid=0,gid=0,fmask=0177,dmask=077,nls=iso8859-1,errors=continue,mft_zone_multiplier=1)
/dev/sda4        /mnt/sda4                ntfs       (ro,relatime,uid=0,gid=0,fmask=0177,dmask=077,nls=iso8859-1,errors=continue,mft_zone_multiplier=1)
/dev/sda5        /mnt/sda5                ntfs       (ro,relatime,uid=0,gid=0,fmask=0177,dmask=077,nls=iso8859-1,errors=continue,mft_zone_multiplier=1)
/dev/sdb1        /mnt/sdb1                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet,errors=remount-ro)
/dev/sdc1        /mnt/sdc1                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=9c669019-ee54-4adb-9af4-9a0d3a103449 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=9c669019-ee54-4adb-9af4-9a0d3a103449 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9c669019-ee54-4adb-9af4-9a0d3a103449 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9c669019-ee54-4adb-9af4-9a0d3a103449 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 9c669019-ee54-4adb-9af4-9a0d3a103449
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5C92D60492D5E316
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 764C4A4E4C4A0977
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
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9c669019-ee54-4adb-9af4-9a0d3a103449 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ae65b526-5325-472f-950b-e9d8fba89374 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  97.527587891 = 104.719450112  boot/grub/core.img                             1
 115.696037292 = 124.227674112  boot/grub/grub.cfg                             1
  98.952404022 = 106.249334784  boot/initrd.img-2.6.38-11-generic              2
  97.655529022 = 104.856825856  boot/initrd.img-2.6.38-8-generic               2
  96.843082428 = 103.984467968  boot/vmlinuz-2.6.38-11-generic                 1
  97.525859833 = 104.717594624  boot/vmlinuz-2.6.38-8-generic                  1
  98.952404022 = 106.249334784  initrd.img                                     2
  97.655529022 = 104.856825856  initrd.img.old                                 2
  96.843082428 = 103.984467968  vmlinuz                                        1
  97.525859833 = 104.717594624  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

hda hdb hdc hdd sdb sdc sdd sde sdf sdg sdh sdi 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by Redblade20XX on 2011-10-13
If you can get into the bios, then you shouldn't have a problem getting another os back on it. Since you can do a live session, you should be able to pull all your important files from the damaged os. store it on a flash drive and reinstall. :p

- Red

---

### Post by tbarton on 2011-10-13
> **Redblade20XX said:**
> If you can get into the bios, then you shouldn't have a problem getting another os back on it. Since you can do a live session, you should be able to pull all your important files from the damaged os. store it on a flash drive and reinstall. :p

- Red

The only versions I've managed to get working are tinycore and LuPuppy, but I don't know those distribution swell and can't figure out how to do anything. With Ubuntu I get the error **No DEFAULT or UI configuration directive found.**


Once I get a Live system up and running, I'd like to install it without overwriting Windows, because hopefully if I can get into a boot menu I'll still be able to save my Windows installation. I'd like to save my existing Ubuntu installation too, but that's not so important as I've not customised it so much. I'm working on the assumption -- though perhaps I'm wrong -- that the operating systems may still work if I can get into a boot menu. It seems unlikely to me that both Windows and Ubuntu became corrupt simultaneously.

---

### Post by ultrageeky on 2011-10-13
Access your BIOS, reset it to its defaults (there will be an option for this), save settings and exit. If that doesn't help, try recreating your boot loader with the [Ultimate Boot Disk]("http://www.ultimatebootcd.com/") (there's a Windows version and a Linux version).

Instead of duel booting it can be better to install Linux then use VirtualBox in Linux to  install Windows or other OS's such that you can boot Linux then, once Linux is loaded, a VirtualBox guest OS without needing to restart your OS to swap between operating systems. This is the method I use. I use Linux most and Windows only when I have no alternative hence I boot Linux then load VirtualBox to load Windows and have both OS's running simultaneously.

Edit to Add:

"**No DEFAULT or UI configuration directive found**"probably relatesto your mouse or keyboard (User Interfaces). Are they wireless or USB? Enable USB Legacy Devices in your BIOS. Try a PS2 mouse and Keyboard if enabling legacy devices fails to help.

---

### Post by sanderd17 on 2011-10-13
Sorry for the late response.

There is nothing wrong with your computer.

I see nothing really weird in your output, apart from the name of your partitions. Normally, GRUB uses names like (hd0,1) or (hd1,3) (resp. for the first partition of the first hard drive and the 3rd partition of the second hard drive). So GRUB doesn't know about sda or sdb. 

So all those lines that look like 
```

set root='(/dev/sda,msdos6)'

```
in your grub.cfg file should probably be changed.

Now, when grub can't read the config file, it should show the grub rescue prompt. I don't know why Grub doesn't do that.

Could you try to rename the file /boot/grub/grub.cfg to /boot/grub/backupgrub.cfg (so you don't lose the file) and then reboot (without USB inserted)? If this shows the grub rescue prompt, than we should be able to repair that grub.cfg file.

btw, the grub rescue prompt looks like this: [http://members.iinet.net.au/~herman546/p15/fig2grub.gif](http://members.iinet.net.au/~herman546/p15/fig2grub.gif)

And for that *No DEFAULT or UI configuration directive found* error, that seems to be an USB problem. Try to use a live CD instead of an USB, or search the forums how to solve it. A lot of people seem the have got this error and were able to solve it.

---

### Post by tbarton on 2011-10-13
I'm afraid I can't boot from CD because it's a netbook without a CD drive. I'll try what you said.

---

### Post by tbarton on 2011-10-13
A problem I have that's preventing me installing a new Linux installation is that GParted won't let me create a fifth partition. Unfortunately I already have four partitions on my hard drive: two main Windows partitions, my Linux partition and a partition that was pre-installed on the machine called "Samsung Recovery". I'd merge the two main Windows partitions if it were possible but I don't know whether it is.

---

### Post by sanderd17 on 2011-10-13
Ok, then we have to look into that error, but first try changing the file name like I said.

For those partitions, you can only have 4 primary partitions. sda3 is an extended partition that contains logical partitions. So a new partition should be put inside sda3.

---

### Post by oldfred on 2011-10-13
You will only be able to create new logical partitions inside the extended partition. 

I do not see anything wrong with your Windows nor Ubuntu partitions from boot script. sda4 does have Windows issue as Windows is not case sensitive and you have duplicate file names (just different cases) which will cause errors.

This is a new style that should work. But I thought I saw a bug report somewhere on it. Natty still uses this device style, but my install of Oneiric has reverted back to hdX style.
set root='(/dev/sda,msdos6)'

BIOS issues, have you done a full power down cold boot? Sometimes that resets more than just a warm boot.

---

### Post by tbarton on 2011-10-13
By "full power down cold boot", do you mean remove the battery and press the on button? If so, I've done that.

I've tried running boot repair. All seemed to be well, but then when I reboot I get "operating system not found". Here's the log: [http://paste.debian.net/136266](http://paste.debian.net/136266)

I did notice than when boot repair was loading I got the message about running chkdsk on the hard drive in Windows. I can't do that if I can't get into Windows though!

sanderd, I tried the file name change you mentioned, but nothing happened. If I'm trying to use boot-repair, maybe I need to change it back again?

---

### Post by oldfred on 2011-10-13
Latest verions shows this in sda2, your window c: drive:
> 
   Boot files:        [COLOR=Red]/grub/grub.cfg[/COLOR] /Windows/System32/winload.exe 
                       [COLOR=Red]/grub/core.img[/COLOR]Those grub files have to be in the Ubuntu partition and in Windows may confuse thing. Not sure if you just copy them back if it will work or if you will have to chroot into your system and total reinstall grub.

Try copying files first. If not chroot into system.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by oldfred on 2011-10-13
You should have a Windows repairCD. If you know anyone with Windows 7 you can make one:

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Another download site Despotism Believed to be ok.
[http://ubuntuforums.org/showpost.php?p=11249721&postcount=439](http://ubuntuforums.org/showpost.php?p=11249721&postcount=439)
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links (Now $10.00):
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by tbarton on 2011-10-13
I've no idea how the Grub folder got on my C drive. I can't delete the grub folder. It's read-only, and  when I try to change the permissions (I'm trying to do this in the LuPu  Live distribution of Linux) it says it can't because it's a read-only  file system. Is there anyway of over-riding this, maybe through the  terminal?

---

### Post by oldfred on 2011-10-13
In Ubuntu it would be sudo nautilus or sudo from command line. Not sure about LuPu?? Be very careful not to delete or move any essential Windows files, only delete the grub and make double sure it contains no windows files somehow.

---

### Post by tbarton on 2011-10-13
> **oldfred said:**
> In Ubuntu it would be sudo nautilus or sudo from command line. Not sure about LuPu?? Be very careful not to delete or move any essential Windows files, only delete the grub and make double sure it contains no windows files somehow.

OK, I deleted that, but still no luck. See paste.debian.net/136286.

Still getting "Operating system not found".

---

### Post by tbarton on 2011-10-13
Here's an update after I selected "Purge and reinstall GRUB": [http://paste.debian.net/136289](http://paste.debian.net/136289)

---

### Post by sanderd17 on 2011-10-13
In any case, I don't get what's wrong.

Can you install a linux os on a new (very small) partition? Normally it should discover other OS that are installed.

I believe you can install Ubuntu on a 4GB partition, so I would create a 5GB partition (just to be sure) and install ubuntu to it.

---

### Post by oldfred on 2011-10-13
It looks like you installed the grub2 boot loader to a partition not to the MBR and now the copy in the MBR is looking for ?? to boot.

The grub.cfg looks ok, so I think just reinstalling grub to the MBR may work.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
[COLOR=Red]sudo mount /dev/sda6 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
[COLOR=Red]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by tbarton on 2011-10-13
I've tried reinstalling the MBR and reinstalling the grub to what I think is the MBR, but to no avail.

paste.debian.net/136331
pastebin.net/B6bunVv2

I'd like to try the recommendation of creating a partition to install Ubuntu on, but I can't create a partition within sda3 because when I open Gparted, sda2 has a padlock. I understand that's because it's mounted, but I can't find a way of unmounting it. The partition doesn't appear in the mounting/unmounting program.

---

### Post by oldfred on 2011-10-13
You have to use a liveCD as you cannot run gparted for the same partition as you boot. Often the liveCD mounts swap and locks the extended partition so you have to click on the swap and right click swapoff.

Your pastebin link is invalid.

---

### Post by tbarton on 2011-10-14
I'll try what you said with GParted. Unfortunately I can't get the Ubuntu Live to run on my computer anyway. I still get the same message about there being no operating system. Maybe I can do a permanent installation of LuPu, since I can get the Live version of that running.

I must have copied down the pastebin link incorrectly. Not sure what the correct version is.

---

### Post by tbarton on 2011-10-14
Well, I finally managed to install LuPu, only to find the same problem: Operating system not found. But just as I was finishing the LuPu installation I realised what a twit I've been...

Since I was having so much trouble booting from USB, I'd filled all the bootable device slots in the BIOS with USB devices. I'd forgotten that my internal hard drive was no longer listed as a bootable device! Very stupid of me. I decided to complete the LuPu installation anyway. It's now booting into Windows, doing lots of checks on drives C: and D:. I hope it works and I've not wrecked anything. At some point I'd like to remove LuPu and have the Ubuntu bootable menu I had before. I presume I just need to run a GRUB configuration in Ubuntu? But that's the least of my worries now.

So now it's time for me to get back to the problem that made everything go wrong in the first place: why my brightness settings have stopped working in Windows 7 (everything went wrong after I tried a system restore).

Anyway, I've learnt a lot about partitions and Linux distributions.

---

### Post by tbarton on 2011-10-15
One last question: I now want to remove LuPu, since I will never use it. Can I simply delete the partition on which it is installed (does that remove the OS cleanly)?

---

### Post by oldfred on 2011-10-15
As long as LuPu is not the system you have booting from the MBR, just deleting or reformating the partition will cleanly remove it. You then can use partition for data or with some effort move partitions around and reuse space depending on where it is. Moving partitions always has a little more risk as a power failure in the middle causes major damage, do have good backups.

If you are booting thru LuPu to Ubuntu, in Ubuntu run this to have Ubuntu's grub2 boot loader in the MBR:

sudo grub-install /dev/sda
sudo update-grub

---

