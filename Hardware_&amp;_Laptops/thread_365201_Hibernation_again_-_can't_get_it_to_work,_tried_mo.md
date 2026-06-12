---
title: "Hibernation again - can't get it to work, tried most tips"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by likeatim on 2007-02-19
Hi,

I'm desperate. I can't get hibernation to work. Let me tell you my story :popcorn: 

My System:
> [LIST]
[*]Dell Inspiron 8600
[*]Ubuntu Edgy (Gnome, no Beryl etc.)
[*]ATI Radeon 9600 (with the drivers installed by Automatix2)
[*]Dual Boot System with Windows XP
[*]Partitions:
[LIST=1]
[*]hda1: NTFS with Windows (Boot Partition)
[*]hda2: ext3 mounted as root
[*]hda3: Swap (primary partition, don't know whether that's important)
[/LIST]
[/LIST]
Hibernation didn't work out of the box.

What I tried so far:
[LIST=1][*]I read about the UUID mysteries, so I did the whole UUID thing with mkswap, changing fstab and dpkg-reconfigure my initramfs. Didn't work. 
[*]I installed suspend2 and played around with it: didn't work.
[*]My current setup:
```
sudo mkswap /dev/hda3
```
```
sudo -i
echo 550959872 > /sys/power/image_size
``` so that 512 MB are reserved for hibernation
```
sudo gedit /etc/fstab
``` putting /dev/hda3 as swap
```
sudo gedit /etc/initramfs-tools/conf.d/resume
```
so that Resume points to /dev/hda3/
```
sudo dpkg-reconfigure linux-image-2.6.17-11-generic
```
[/list]
Still, suspend does work, but when I try to hibernate, it just switches to a login screen.
I'm desperate and don't know what else to try out. Or is hibernation currently just not working?

any help greatly appreciated!

cheers

---

### Post by tgalati4 on 2007-02-20
Dear likeatim,

Does standby or suspend work properly?  I have an older Dell Inspiron 7500 that works in both suspend and hibernate.  

Hibernate is a deeper form of sleep where the memory snapshot is written to disk.  Upon wakeup this image is reread.  On my system, I only save a few seconds from hibernate to a booting from cold.  Strange, so I don't use it.  I either leave my machine in standby all the time and plugged in or I shut down if I'm not going to use the machine for a while.

Hibernate is useful to keep 150 Firefox tabs open and anything else running when you return to your work session.

An alternative is to set "save session" under system--admin---sessions and this will save the state of many applications upon boot up.

There are also hibernation switches that are turned off by default in Ubuntu because of obvious hardware problems, but I can't find them right now.  They are buried in a config file.

Sometimes it's the external hardware that causes problems--wireless cards, dongles, anything plugged in.  Try removing all of these first to get hibernate to work.

Also, Dell's tend to use a specific hibernation file and this may be the problem.  There's a Dell utility to create this file.  It's possible that this file needs to be located on specific tracks of the drive.  Your partition scheme may not allow this.  The bios controls this behavior so putting Windows in hibernate may exclude Ubuntu from going into hibernate.  

My system has an old Win 98 install and on bootup I get a bios error message saying that the hibernate file can't be found.  (I probably lost it when moving partitions around).  I don't use it (since I don't use Windows) and maybe this is the difference between hiberate working or not.

Keep trying,

Terry

---

### Post by likeatim on 2007-02-21
thanks for your reply
> **tgalati4 said:**
> Dear likeatim,

Does standby or suspend work properly?  I have an older Dell Inspiron 7500 that works in both suspend and hibernate. 
Standby works. I thought standby = suspend? Can't find it in the Exit Menu?

> **tgalati4 said:**
> Hibernate is a deeper form of sleep where the memory snapshot is written to disk.  Upon wakeup this image is reread.  On my system, I only save a few seconds from hibernate to a booting from cold.  Strange, so I don't use it.  I either leave my machine in standby all the time and plugged in or I shut down if I'm not going to use the machine for a while.
I wouldn't know that since it doesn't work :lolflag: 

> **tgalati4 said:**
> Hibernate is useful to keep 150 Firefox tabs open and anything else running when you return to your work session.
An alternative is to set "save session" under system--admin---sessions and this will save the state of many applications upon boot up.
Good idea, even if not the same!

> **tgalati4 said:**
> There are also hibernation switches that are turned off by default in Ubuntu because of obvious hardware problems, but I can't find them right now.  They are buried in a config file.
Sometimes it's the external hardware that causes problems--wireless cards, dongles, anything plugged in.  Try removing all of these first to get hibernate to work.
Also, Dell's tend to use a specific hibernation file and this may be the problem.  There's a Dell utility to create this file.  It's possible that this file needs to be located on specific tracks of the drive.  Your partition scheme may not allow this.  The bios controls this behavior so putting Windows in hibernate may exclude Ubuntu from going into hibernate.  
- no external devices whatsoever
- I had Ubuntu on the machine a year ago (before I removed it again), back then it worked (even as slow as you described though) - that's the strange thing...
- I haven's seen a specific hibernation file anywhere on a partition manager - or would it be invisible there?

---

### Post by hardyn on 2007-02-21
add vga=791 to boot string... i have had to do this with ALL my edgy installs to make it hybernate.

---

### Post by likeatim on 2007-02-21
ok, I'll try that...
I just now realized that the systemmonitor doesn't display any swap filesystem - is that normal?
I had done the
mkswap /dev/hda3
adding the UUID to /etc/fstab
adding the UUID to the resume file
and reconfiguring the initram-fs

---

### Post by shotgunefx on 2007-02-21
I just installed Edgy on my Dell Inspiron 8600 a few weeks ago and everything works out of the box. 

It's in my car at the moment (carpc), but if you want, let me know if you want to see any specific setting and I'll be more than happy to help.

BTW, I have the nvidia (5200?) not the ATI.

---

### Post by tgalati4 on 2007-02-21
This is a reach--there are two types of swap files.  A specific partition that is created by the user with a partitioner, designated as type "swap" that Linux detects during device scanning.  The second type is created internally by Linux when an external swap partition is not found.  It is possible that hibernate will only work with a real swap partition, not a virtual one.  I have not seen the hibernate file either--so I assume that it is kept on the swap partition.  It only becomes an issue when it doesn't work!

---

### Post by likeatim on 2007-02-21
> **shotgunefx said:**
> I just installed Edgy on my Dell Inspiron 8600 a few weeks ago and everything works out of the box. 

It's in my car at the moment (carpc), but if you want, let me know if you want to see any specific setting and I'll be more than happy to help.

BTW, I have the nvidia (5200?) not the ATI.
that would be very helpful. I have an ATI since they had to replace some parts at Dell.
I'd be interested in:
/etc/fstab
/etc/initramfs-tools/conf.d/resume
/boot/grub/menu.lst
and especially your partitioning.

sudo fdisk -l on my system gives me this:
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4983    40025916    7  HPFS/NTFS
/dev/hda2            4984        7062    16699567+  83  Linux
/dev/hda3            7063        7296     1879605   82  Linux swap / Solaris
```
So I don't understand why the systemmonitor doesn't see a swap file or partition...?!

---

### Post by hardyn on 2007-02-21
there was a thread some time ago about edgy not enabling swap by default... it was rare, but not isolated.  from what i remember it was easy to fix, but there was no conclusion as to why this was happening.

---

### Post by tgalati4 on 2007-02-22
If you don't need the Beryl eye-candy,  perhaps you should consider installing Dapper Drake 6.06 LTS.  See if the swap gets detected automatically and if hibernation works properly.  Dell laptop standby and hibernation is generally well supported in Ubuntu.  There is some weirdness with peripherals and order of power on, but there are work arounds that have been posted.

---

### Post by likeatim on 2007-02-22
> **hardyn said:**
> add vga=791 to boot string... i have had to do this with ALL my edgy installs to make it hybernate.
I tried that, did not work. I still get a login screen immediately.

---

### Post by tgalati4 on 2007-02-22
Check the BIOS (F2? perhaps) and see if the power management is even turned on.  Set up some reasonable values.  This will automatically put the machine in hibernate mode, unless overridden by the OS.  

Post the output of dmesg | grep ACPI

Try a Dapper Drake 6.06.1 Live CD, turn on power management through preferences-->power management.  Set reasonable values, and see if it works.  

If it works in Dapper with the Live CD, then install Dapper.  

Either way, let us know.  Now we are curious.

---

### Post by shotgunefx on 2007-02-22
> **likeatim said:**
> that would be very helpful. I have an ATI since they had to replace some parts at Dell.
I'd be interested in:
/etc/fstab
/etc/initramfs-tools/conf.d/resume
/boot/grub/menu.lst
and especially your partitioning.

sudo fdisk -l on my system gives me this:
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4983    40025916    7  HPFS/NTFS
/dev/hda2            4984        7062    16699567+  83  Linux
/dev/hda3            7063        7296     1879605   82  Linux swap / Solaris
```
So I don't understand why the systemmonitor doesn't see a swap file or partition...?!

I thought you jinxed me. I pulled it out of the car and it wasn't working anymore. It turned out to be a using nvidia-xconfig which changed the loaded modules when I ran it. Restoring them fixed it (though I seemed to have to boot a few times before it worked), though like a champ now. I will say though, that hibernation is pretty slow for when waking up.

root@coupe:/#cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda4
UUID=6ef887e4-f2c0-458a-88f1-7f7de04fff52 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=26ac5353-7a4e-4bb8-bf21-1fe7ff7f42bf /mymedia          ext3    defaults        0       2
# /dev/hda5
UUID=20f65c6b-b5a3-49b7-87a4-8e4b36643546 none            swap    sw              0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
root@coupe:/# cat /etc/initramfs-tools/conf.d/resume```

RESUME=UUID=20f65c6b-b5a3-49b7-87a4-8e4b36643546

```
root@coupe:/# fdisk -l```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5915    47512206   83  Linux
/dev/hda2            7109        7187      634567+   5  Extended
/dev/hda4            5916        7108     9582772+  83  Linux
/dev/hda5            7109        7187      634536   82  Linux swap / Solaris

```
menu.1st```

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         2

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=6ef887e4-f2c0-458a-88f1-7f7de04fff52 ro
# kopt_2_6=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=788

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20 root=/dev/hda4 ro quiet splash vga=788
initrd          /boot/initrd.img-2.6.20
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.20 (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20 root=/dev/hda4 ro single
initrd          /boot/initrd.img-2.6.20
boot

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,3)
kernel          /boot/vmlinuz- 2.6.17-11-generic root=/dev/hda4 ro quiet splash vga=788
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda4 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------

```

Here's the differing modules section in case it's of any use to you.
```

Module section that worked....
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
------------------------------
Module section that caused problems...
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

```

Hope this helps.

-Lee

---

### Post by hardyn on 2007-02-22
is it possible that 'sever' has been downloaded? and their is no gui?

---

### Post by likeatim on 2007-03-02
> **hardyn said:**
> is it possible that 'sever' has been downloaded? and their is no gui?
...meaning what...?

---

### Post by tgalati4 on 2007-03-03
I have found waking from hibernation almost as slow as doing a cold boot.  My understanding of hibernation is that the file system writes a memory snapshot to a file (perhaps in /swap, I really don't know) .  Upon booting, the kernel detects this memory snapshot and reloads it into memory.  This can take a loooong time.  As a result I always use "suspend" and make sure it is plugged in.  It will go into hibernation if the battery is critically low.  

This way it will keep all of my browser sessions current with a safety if the battery runs out.

It would be nice to make some improvements in hibernation speed, but with so many different models of laptops, there is hardly a standard to work with.

---

### Post by likeatim on 2007-03-04
I found my solution:
[LIST=1]
[*]Installed suspend2
[*]added the "resume2=swap:/dev/hda3" to the relevant kernel entry in /boot/grub/menu.lst
[*]made in /etc/hibernate/common.conf this: ```
### fbsplash (enable SwitchToTextMode if you use this)
# FBSplash on
# FBSplashTheme suspend2
```
[*]activated in /etc/hibernate/suspend2.conf```
## useful for initrd usage:
SuspendDevice swap:/dev/hda3

## Powerdown method - 3 for suspend-to-RAM, 4 for ACPI S4 sleep, 5 for poweroff
PowerdownMethod 5

## Or traditionally like this:
Suspend2AllSettings 0 0 2056 65535 5

# ProcSetting userui_program /usr/bin/suspend2ui_usplash
ProcSetting userui_program /usr/bin/suspend2ui_text
```
[*]and changed 2 scripts according to [http://gentoo-wiki.com/HOWTO_Software_Suspend_v2#Using_gnome-power-manager](http://gentoo-wiki.com/HOWTO_Software_Suspend_v2#Using_gnome-power-manager)[/LIST]
that way I can now either push the power button or close the lid to hibernate. it also hibernates on low power.

> **tgalati4 said:**
> I have found waking from hibernation almost as slow as doing a cold boot.  My understanding of hibernation is that the file system writes a memory snapshot to a file (perhaps in /swap, I really don't know) .  Upon booting, the kernel detects this memory snapshot and reloads it into memory.  This can take a loooong time.  As a result I always use "suspend" and make sure it is plugged in.  It will go into hibernation if the battery is critically low.  
try suspend2. it's blazing fast (hibernation and resuming takes between about 10 seconds)

---

