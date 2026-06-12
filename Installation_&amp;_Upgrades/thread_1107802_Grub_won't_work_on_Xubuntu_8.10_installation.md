---
title: "Grub won't work on Xubuntu 8.10 installation"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by digitaleagle on 2009-03-27
I can't get my Xubuntu 8.10 to boot for some reason.  It stops at “grub loading stage 1.5&#8243;.

I initially thought it had to do with my hardware upgrade (I added an SATA controller and hard drive), but I am able to install Xubuntu 8.04 and it boots with no problem.

I have installed multiple times, and I verified that it is creating the partition on the drive and putting files on it.  So, it seems to be a grub issue to me rather than an install issue.

I have also tried reinstalling Grub after the fact as well.  I tried booting off both the Xubuntu 8.04 and 8.10 and going through the steps to install Grub to the master boot sector.

I also documented it here: [http://linuxsagas.wordpress.com/2009/03/17/grub-boot-error/]("http://linuxsagas.wordpress.com/2009/03/17/grub-boot-error/")

Any thoughts on what I am missing?  Thanks.

---

### Post by Mark Phelps on 2009-03-27
Are you dual-booting by any chance? And, if so, is it with Vista?  I'm asking because there's a documented problem with Vista that causes it to wipe out GRUB so it hangs on that error message.

---

### Post by digitaleagle on 2009-03-30
Thanks for the thought, Mark.  No, I am not dual booting.  This is an older computer that I just want for Internet access.  The only two partitions are the main ext3 partition and the swap partition.  I chose the auto partition during the install.

---

### Post by digitaleagle on 2010-06-24
I am back working on this again.  I ended up putting FreeBSD on the computer, and it worked for a while.  Just yesterday, I decided to try Ubuntu 10.04.  I get the same problem:  it hangs before loading grub.

I think the issue has something to do with grub2.  Here are some articles that I have found helpful,  but I still can't find the answer yet:

These are the instructions for the old grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

These are the instructions for the new grub:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

When I get the opportunity, this is my next step:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


Also, if anyone knows a good link with instructions for trying to install lilo from the Live CD, I would love to try that.

If I find anything, I will post back.

---

### Post by digitaleagle on 2010-06-24
boot info script output (from Live CD):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2         154,302,464   156,301,311     1,998,848  82 Linux swap / Solaris
/dev/sda3             976,896   154,300,415   153,323,520  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        1f4dd6fc-3ebd-496a-9930-c7c3c0cf96e1   ext2                                     
/dev/sda2        43264d44-bb98-40b6-bbc6-c1a7b5ab853c   swap                                     
/dev/sda3        baaee594-5033-4503-9426-35347a32d61d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set baaee594-5033-4503-9426-35347a32d61d
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1f4dd6fc-3ebd-496a-9930-c7c3c0cf96e1
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1f4dd6fc-3ebd-496a-9930-c7c3c0cf96e1
	linux	/vmlinuz-2.6.32-21-generic root=UUID=baaee594-5033-4503-9426-35347a32d61d ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1f4dd6fc-3ebd-496a-9930-c7c3c0cf96e1
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=baaee594-5033-4503-9426-35347a32d61d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1f4dd6fc-3ebd-496a-9930-c7c3c0cf96e1
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1f4dd6fc-3ebd-496a-9930-c7c3c0cf96e1
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-21-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=baaee594-5033-4503-9426-35347a32d61d /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=43264d44-bb98-40b6-bbc6-c1a7b5ab853c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by digitaleagle on 2010-06-25
Trying some stuff in this article:
[http://alicious.com/2009/grub-2-install-error-15/](http://alicious.com/2009/grub-2-install-error-15/)

And, trying the Error 15 stuff in this article:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by digitaleagle on 2010-09-24
I have since blown this installation and decided to Ubuntu instead of Xubuntu.  I tried both Ubuntu 10.04 and Ubuntu 10.10 beta with no luck.  I opened another thread since I am now on Ubuntu:
[http://ubuntuforums.org/showthread.php?p=9885240#post9885240](http://ubuntuforums.org/showthread.php?p=9885240#post9885240)

---

