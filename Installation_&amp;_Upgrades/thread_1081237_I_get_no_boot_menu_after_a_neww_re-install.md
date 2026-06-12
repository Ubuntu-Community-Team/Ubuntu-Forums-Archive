---
title: "I get no boot menu after a neww re-install"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by bsprowl on 2009-02-26
I tried to find the scrip but got the following result:

bsprowl@Lenovo-T60:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for bsprowl: 
bash: /home/bsprowl/Desktop/boot_info_script*.sh: No such file or directory
bsprowl@Lenovo-T60:~$

Any suggestions?

Bob

---

### Post by time_bomb on 2009-02-26
> **bsprowl said:**
> I tried to find the scrip but got the following result:

bsprowl@Lenovo-T60:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for bsprowl: 
bash: /home/bsprowl/Desktop/boot_info_script*.sh: No such file or directory
bsprowl@Lenovo-T60:~$

Any suggestions?

Bob
You can try this firstly :cd Desktop
then:sudo bash

I think it's no question.

hope it can help you

---

### Post by bsprowl on 2009-02-26
Go the same result, file not found.

I've re-installed Ubuntu six times in the last three days. I had an earlier thread on this problem that had no useful suggestions. The latest installation still does not find a boot menu must a Grub problem.  

Unforunately I haven't not been able to delete Ubuntu so I have had to rebuild the Windows installation from back ups but this is getting old as it takes three hours.

And I 'm no closer to solving it.  I tried several various guided and unguided and manual instllations with Windows completely disappearing
a couple of times.  

Nothing has changed from the eariler thread as far as Grub file contents go.

Bob

---

### Post by caljohnsmith on 2009-02-26
Have you actually downloaded the Boot Info Script to your desktop first before running the command from your first post? You can download it from:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

---

### Post by bsprowl on 2009-02-26
I honestly didn't know I had to download it.  I have no idea what it did; I saw in another thread and thought it would help.  I downloaded it and this is what I got.

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf990c72

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   118,784,609   118,784,547   7 HPFS/NTFS
/dev/sda4         118,784,610   625,137,344   506,352,735   f W95 Ext d (LBA)
/dev/sda5         131,090,463   179,911,934    48,821,472  83 Linux
/dev/sda6         375,214,203   376,852,769     1,638,567  82 Linux swap / Solaris
/dev/sda7         376,852,833   625,137,344   248,284,512   7 HPFS/NTFS
/dev/sda8         179,911,998   375,214,139   195,302,142  83 Linux
/dev/sda9         118,784,736   131,090,399    12,305,664  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F858A28558A2426C" LABEL="Preload" TYPE="ntfs" 
/dev/sda5: UUID="2727406d-035b-4db9-8682-2eb17fc96db3" TYPE="ext3" 
/dev/sda6: UUID="acdac8aa-36ae-4913-bb49-47a747784d66" TYPE="swap" 
/dev/sda7: UUID="F2ACB04AACB00ADD" TYPE="ntfs" 
/dev/sda8: UUID="22ce1b28-8b3f-4096-988d-88294002b46c" TYPE="ext3" 
/dev/sda9: UUID="32a4d52f-1200-4f43-b4c4-236f24fe452b" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda8 on /home type ext3 (rw,relatime)
/dev/sda9 on /tmp type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=0755)
gvfs-fuse-daemon on /home/bsprowl/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bsprowl)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2727406d-035b-4db9-8682-2eb17fc96db3

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2727406d-035b-4db9-8682-2eb17fc96db3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=22ce1b28-8b3f-4096-988d-88294002b46c /home           ext3    relatime        0       2
# /dev/sda9
UUID=32a4d52f-1200-4f43-b4c4-236f24fe452b /tmp            ext3    relatime        0       2
# /dev/sda6
UUID=acdac8aa-36ae-4913-bb49-47a747784d66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  74.9GB: boot/grub/menu.lst
  75.0GB: boot/grub/stage2
  75.0GB: boot/initrd.img-2.6.27-11-generic
  74.9GB: boot/initrd.img-2.6.27-7-generic
  74.9GB: boot/vmlinuz-2.6.27-11-generic
  74.9GB: boot/vmlinuz-2.6.27-7-generic
  75.0GB: initrd.img
  74.9GB: initrd.img.old
  74.9GB: vmlinuz
  74.9GB: vmlinuz.old

I will see if I can figure out what it tells me.

Bob

---

### Post by caljohnsmith on 2009-02-26
So what exactly happens on start up? At what point do you actually see some text or something? How about next time you reboot, press the down arrow key repeatedly; does that boot you into Windows?

---

### Post by bsprowl on 2009-02-26
I powered off and then pulled the battery for a few seconds.

Installed the battery and pushed the power on button.  The small icons tha show disk and system activity blinked on and off a time or two, the system paused for 20 or 30 seconds and then disk activity began for another 30 seconds or so and the screen came up, first with the Ubuntu pink( or whatever color youcare to call it) and then with the wallpaper that was imported from Windows (that's got to go!).  

No Thinkpad option to go to the BIOS (that's puzzling also) and no menu.  Just directly into Ubuntu. 

Tried it again while repeatedly pressing the down arrow key with the same results - Ubuntu.

Did another cold boot (power off and battery out) and tried it again pressing the down arrow repeatedly and got into Windows! So the menu is there but I can't see it.  And a warm re-boot apparently uses the last boot (doesn't go to to the boot menu).  Lots to think about. 

I've got to stop and pack for a trip tomorrow but will follow up in a day or two.  

Thanks

Bob

---

### Post by caljohnsmith on 2009-02-27
That is really strange, but at least you were able to confirm the Grub menu does exist (but is just not visible) by booting into Windows when you pressed the down arrow key. Do you know which function key to press on start up to get into your BIOS? That would be the first place I would start to see if you can even access your BIOS. You also might want to consider getting a BIOS upgrade, or if you have the latest BIOS, at least reflashing the latest version of BIOS to your computer in case it is somehow corrupt right now. Anyway, when you get a chance to troubleshoot it again, let me know how it goes.

---

### Post by congew on 2009-05-20
> **bsprowl said:**
> 
No Thinkpad option to go to the BIOS (that's puzzling also) and no menu.  Just directly into Ubuntu. 

Tried it again while repeatedly pressing the down arrow key with the same results - Ubuntu.

Did another cold boot (power off and battery out) and tried it again pressing the down arrow repeatedly and got into Windows! So the menu is there but I can't see it.  And a warm re-boot apparently uses the last boot (doesn't go to to the boot menu).  Lots to think about. 

Hi, Bob,

I recently got the exactly same problem as yours. My laptop is T60 and has both XP and ubuntu 8.04 installed. After my upgrade from 8.04 to 8.10 and reboot, there is no thinkpad option screen, no grub menu (always blackscreen). After several seconds waiting, it just goes directly into Ubuntu. 

Below is what I did to fix that: 
1. powered off the computer and took the battery off. 
2. pressed down and hold the power button for at least 20 seconds. 
3. replaced the battery and power cord.
4. turned on the computer and now everything goes fine: the Thinkpad logo screen, the grub menu options ......

Hope that helps.

---

