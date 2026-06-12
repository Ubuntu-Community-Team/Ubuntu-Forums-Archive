---
title: "N00b, I just installed ubuntu and my vista install is gone?"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by TheRev813 on 2009-06-09
Ok so I just installed ubuntu onto an old windows xp drive I had, formatting it first. I got it working fine, still playing around with it, but now I can't boot into vista. My vista hard drive is a 500gb, and no matter what I can't boot into it. I unplugged the ubuntu drive, still no luck. It looks like "windows vista loader" is in the grub, but I cannot use the arrow keys to navigate to it and select it, however my keyboard works fine in the bios, any ideas?

---

### Post by drew2222 on 2009-06-09
When you installed Ubuntu did you set the Language and Region options correctly and test your keyboard for correct output during install?
Are you using a normal ps2 keyboard or is it USB? 
These may not answer your problem, just ideas. I have installed Ubuntu on 2 machines and am very pleased so far with the results.

---

### Post by yaroto98 on 2009-06-09
Have you waited a bit, clicked randomly, and tried again? (I have to do that for one of my keyboards) it takes a while to load.

---

### Post by TheRev813 on 2009-06-09
It is a USB keyboard, the backlit Saitek Eclipse to be exact. It'll work fine in the BIOS, but no where else. Also when the Ubuntu hard drive is disconnected I get the same thing, the Grub manager

---

### Post by merlinus on 2009-06-09
That's because grub was installed into the mbr on your 500G vista drive.  What is the booting order of your hdds in bios?

Also, post results of these terminal commands whilst in ubuntu:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by TheRev813 on 2009-06-09
My booting order has been changed back and forth with no success, now its set to boot from the vista drive first. Here are the results from sudo fdisk -l

billy@Billy-Ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e28b981

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2bbc2bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23330   187398193+  83  Linux
/dev/sdb2           23331       24321     7960207+   5  Extended
/dev/sdb5           23331       24321     7960176   82  Linux swap / Solaris
billy@Billy-Ubuntu:~$ 



And from the other....

billy@Billy-Ubuntu:~$ cat /boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d87c2550-f1dc-4d90-86bb-d453ac899c21 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d87c2550-f1dc-4d90-86bb-d453ac899c21

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d87c2550-f1dc-4d90-86bb-d453ac899c21
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d87c2550-f1dc-4d90-86bb-d453ac899c21 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d87c2550-f1dc-4d90-86bb-d453ac899c21
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d87c2550-f1dc-4d90-86bb-d453ac899c21 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d87c2550-f1dc-4d90-86bb-d453ac899c21
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

billy@Billy-Ubuntu:~$ 



This is all foreign to me lol. I'm really good on PCs. build em, troubleshoot, fix, etc. Thanks for all the help. I'm trying to broaden my horizons.

---

### Post by merlinus on 2009-06-09
This all looks correct, and theoretically should work as long as your vista hdd is first in the booting order.

But let's try this, whilst in a terminal in ubuntu.  

```

sudo grub
find /boot/grub/stage1
quit

```

It should be something like (hd1,0)

---

### Post by ad_267 on 2009-06-09
If you edit the /boot/grub/menu.lst file you can change the "default 0" line to "default saved" so that it will boot into Vista. You will need superuser privileges to do this, you can press Alt+F2 and run "gksu gedit /boot/grub/menu.lst". gksu runs a command as root, and gedit is the text editor to use. It would be nice to get grub to recognise your keyboard of course though.

Edit: A few posts I've found say that enabling USB legacy keyboard support in your BIOS might fix this (even when the keyboard works in the BIOS).

---

### Post by TheRev813 on 2009-06-10
The keyboard trick did it, thanks for everything! Now I'd like to get Beryl going, but I'll tackle that later:biggrin:

---

### Post by ad_267 on 2009-06-10
> **TheRev813 said:**
> The keyboard trick did it, thanks for everything! Now I'd like to get Beryl going, but I'll tackle that later:biggrin:

Beryl was merged back into Compiz a long time ago. It's part of Compiz fusion which is installed by default. Usually you just have to enable your video drivers under System - Administration - Hardware Drivers. Then you can install the compizconfig-settings-manager to be able to configure compiz and enable the different effects.

This thread is a good resource: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by TheRev813 on 2009-06-15
Yeah that's pretty cool I've been messing around with it, thanks.

---

