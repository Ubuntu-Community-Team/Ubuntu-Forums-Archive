---
title: "I can't boot!!! PLEASE!!! Help its been 2 weeks!"
date: 2010-04-19
forum: Hardware
---

### Post by Jus512 on 2010-04-19
I have a HP Pavilion Dv5 , with Karmic Koala 9.10, the specs are Intel Core 2 duo 2.4ghz, 4gb ram and a Nvidia Geforce 9600GT.

Anyway the problem is that whenever I turn on my laptop, I get a black screen with a blinking dash on the upper left corner of a screen, so I waited and waited and nothing happens, it won't boot.

So I found out that pressing alt + F1 shows some text and it said "usplash: no usable theme found for 1024x768 screen init failed" 

I tried many fixes but none worked. I worked so hard on perfecting my Ubuntu OS for myself and it would be a shame to make a clean install!

---

### Post by wilee-nilee on 2010-04-19
I would try a live cd to make sure it's not a hardware issue. Beyond that hopefully you can get some help.

---

### Post by Jus512 on 2010-04-19
What do mean? I tried using the livecd to "Try Ubuntu without installing" and did numerous thing in order to fix my Ubuntu, none avail. =(

---

### Post by wilee-nilee on 2010-04-19
> **Jus512 said:**
> What do mean? I tried using the livecd to "Try Ubuntu without installing" and did numerous thing in order to fix my Ubuntu, none avail. =(

Just trying to confirm what you have done in trying to fix the problem. Generally the people who are good at fixing boot problems suggest a post of this script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
If you can remember some of what you tried it might be relevant so keep that info available, basically because questions will probably be asked.

---

### Post by Jus512 on 2010-04-19
Thank you Good sir!!! I hope someone can help me!

heres the code

```

```Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swsupend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'swsupend'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c0d9f0a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   207,591,423   207,384,576   7 HPFS/NTFS
/dev/sda3         207,591,930   606,999,959   399,408,030  83 Linux
/dev/sda4         606,999,960   625,137,344    18,137,385   5 Extended
/dev/sda5         607,000,023   625,137,344    18,137,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D61C5CB51C5C91FB                       ntfs       System Reserved               
/dev/sda2        5CF475E1F475BDB8                       ntfs                                     
/dev/sda3        fdb66f77-7b08-479d-b404-99530c8059fa   ext4                                     
/dev/sda5        fd4eae05-bf55-4001-8195-eecce34241e5   swsupend                                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set fdb66f77-7b08-479d-b404-99530c8059fa
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set fdb66f77-7b08-479d-b404-99530c8059fa
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=fdb66f77-7b08-479d-b404-99530c8059fa ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set fdb66f77-7b08-479d-b404-99530c8059fa
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=fdb66f77-7b08-479d-b404-99530c8059fa ro single  splash vga=791
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set fdb66f77-7b08-479d-b404-99530c8059fa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fdb66f77-7b08-479d-b404-99530c8059fa ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set fdb66f77-7b08-479d-b404-99530c8059fa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fdb66f77-7b08-479d-b404-99530c8059fa ro single  splash vga=791
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fdb66f77-7b08-479d-b404-99530c8059fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fd4eae05-bf55-4001-8195-eecce34241e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 106.8GB: boot/grub/core.img
 124.2GB: boot/grub/grub.cfg
 109.4GB: boot/initrd.img-2.6.31-14-generic
 109.4GB: boot/initrd.img-2.6.31-20-generic
 106.8GB: boot/vmlinuz-2.6.31-14-generic
 107.3GB: boot/vmlinuz-2.6.31-20-generic
 109.4GB: initrd.img
 109.4GB: initrd.img.old
 107.3GB: vmlinuz
 106.8GB: vmlinuz.old```

```

---

### Post by andrewthomas on 2010-04-19
You neglect to mention that you installed windows after installing ubuntu.  I assume that you can boot to windows with no problem?  What happened to your swap partition?

```
sda5: 

    File system:       swsupend
```
First, you need to reinstall grub2 from the Live cd using the instructions here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
under the 
**Reinstalling GRUB 2**

[SIZE=4]SIMPLEST - Copy  GRUB 2 Files from the LiveCD[/SIZE]

section.  Your ubuntu root now is on sda3 where it used to be on sda1

---

### Post by Jus512 on 2010-04-19
Yes, I did forget to mention but, you see even with Windows installed it was working fine for weeks until one day I decided to hibernate my laptop and then after that this happened.

---

### Post by andrewthomas on 2010-04-19
What happens when you try to reinstall grub2 to the MBR?

---

### Post by Jus512 on 2010-04-19
> **andrewthomas said:**
> What happens when you try to reinstall grub2 to the MBR?

Didn't work, same problem, screen init failed and cant boot

---

### Post by utnubuuser on 2010-04-19
Well,... this is a kinda lame solution, but since you've got 320gig drive, I'd be inclined to load the liveCD, open the partition editor, shrink the very right-hand partition towards the left by 5gigs, then install Ubuntu to the unused space.  That should then make the system bootable, and will give you a new grub from which you can fix/compare the original installation.

You could also read up on how to boot manually, but to boot manually you have to be able to at least access grub.

You could also try using something along the lines of SuperGrub on a liveCD and see if it'll find the bootable kernels.

Oh, and if this was after "hibernate" it might be as simple as an invalid hibernate/resume file sitting somewhere that's blocking grub.  - I don't use hibernate, so I'm not all that familiar with it, but I'm fairly sure that when you hibernate a system, a 'resume' file is written somewhere from which your processes are resumed -  it might be that file causing the issue.  - Instead of booting normally, the machine might be trying to resume from 'sleep'

Seem to remember something along the lines of a 'resume' file being written to /var????

---

### Post by Jus512 on 2010-04-19
> **utnubuuser said:**
> Well,... this is a kinda lame solution, but since you've got 320gig drive, I'd be inclined to load the liveCD, open the partition editor, shrink the very right-hand partition towards the left by 5gigs, then install Ubuntu to the unused space.  That should then make the system bootable, and will give you a new grub from which you can fix/compare the original installation.

You could also read up on how to boot manually, but to boot manually you have to be able to at least access grub.

You could also try using something along the lines of SuperGrub on a liveCD and see if it'll find the bootable kernels.

Oh, and if this was after "hibernate" it might be as simple as an invalid hibernate/resume file sitting somewhere that's blocking grub.  - I don't use hibernate, so I'm not all that familiar with it, but I'm fairly sure that when you hibernate a system, a 'resume' file is written somewhere from which your processes are resumed -  it might be that file causing the issue.  - Instead of booting normally, the machine might be trying to resume from 'sleep'

Seem to remember something along the lines of a 'resume' file being written to /var????

Eh, this too much work, maybe I should just reinstall ubuntu...

Are you guys sure, there is no alternative?

---

### Post by Mark Phelps on 2010-04-19
Since you apparently do not have GRUB installed to your MBR, how were you getting an OS selection menu?  My guess, from the disk info, is that you've modified the Win7 BCD to add an entry for Ubuntu. Right?

You said it was working in Win7 until you hibernated, so did you by any chance hibernate using one OS but upon restart, choose the other instead?

Asking this second question because there have recently been a rash of "just resumed from hibernation and can't boot anymore" kind of posts lately in which everyone admitted to just this problem.

Notice that Win7 is installed to two partitions -- which, AFAIK, only happens by default when Win7 is installed to an EMPTY hard drive.  So, it looks like you installed Win7 to a blank drive and THEN you installed Ubuntu -- and in that case, you wrote GRUB into the first Linux partition, not your MBR.

I know none of this is what you're saying -- but it's what the info in the script results indicates.

Short of reinstalling your OSs (LOTS or work!), my suggestion to get a working system back (if you can't boot into anything) is to boot from a Win7 DVD amd run Startup Repair three times.  That will repair the boot loader files, the BCD, and the MBR -- and should get you booting again.

If you don't have a Win7 DVD, go to the link below and download the proper Win7 image and burn it to CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by Yellow Pasque on 2010-04-19
If you press 'Esc' to get into grub and edit your boot options from 'quiet splash' to 'nosplash', do you get it to boot or different error messages?

---

### Post by Jus512 on 2010-04-20
> **Temüjin said:**
> If you press 'Esc' to get into grub and edit your boot options from 'quiet splash' to 'nosplash', do you get it to boot or different error messages?


Thanks I will try later when I get home!

---

### Post by Jus512 on 2010-04-20
Ok I tried that it still displays the same thing

---

### Post by LucianoMS on 2010-04-20
Have you tried the rescue mode?

Does this option appear in the option list?

---

### Post by Jus512 on 2010-04-21
> **LucianoMS said:**
> Have you tried the rescue mode?

Does this option appear in the option list?

How do I do this?

---

### Post by kyreks4 on 2010-04-21
First lesson: NEVER install Windows after Linux (or most other OS's for that matter) Windows normally detects grub, decides that it is not part of Windows and is possibly harmful, and removes/tries to remove it...

Windows doesn't like to play nice with others...

What I am going to do when I get Windows 7:

either fdisk and install 7, and then Linux distro(s)

or "copy" my Distros elsewhere (i cannot remember correct term) install Windows, and then install distro (either by burning an image of my distro or "copying" and reinstalling my user folder)

what i suggest you do: boot Windows, format partitions that aren't Windows, and then install whichever *nix distros you like....

you could always try to make an image or "clone" i think the term is, of your Ubuntu, format all partitions that aren't part of Windows, and reinstall...

---

