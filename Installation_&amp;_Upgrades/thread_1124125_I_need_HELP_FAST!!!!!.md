---
title: "I need HELP FAST!!!!!"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by Drumm3r4lyfe on 2009-04-13
Alright I'm in a bit of an odd problem.

I recently installed 8.10 ubuntu, after deleating 8.04 wubi manually. I was dual booting between windows xp and ubuntu using a nice and simple boot list which had windows xp first. But now ubuntu is first after using the cd to install it, and I cannot seem to find the xp I had been booting into.

Is there anyway I can change the os boot order? I think ubuntu deleted everything on my c drive. Idk im really confused right now.

I thought I could just make a small 6 gb partition for ubuntu on my c drive and install it on there. now it's showing a 6 gb drive on my desktop?? 

I really want to get windows xp back or my parents will get really mad at me. Can I somehow system recover to get xp back, or just delete ubuntu just for now?

I really need help fast. 

Thanks.

---

### Post by lisati on 2009-04-13
First of all, we need to check if Windows is actually there. If it's not showing in the boot-up menu, chances are it has gone. Please post the output from the command:```
sudo fdisk -l
```
This will help us know how your computer's hard drive is organized and give some clues as to what's on it as far as Windows, Ubuntu etc..... are concerned.

---

### Post by Drumm3r4lyfe on 2009-04-13
```
ubuntu@ubuntu:~$ sudo fdisk -l
[sudo] password for ubuntu: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcebaceba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5168    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97a82cd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1836    14747638+   c  W95 FAT32 (LBA)
/dev/sdb2            3400       32119   230693400    7  HPFS/NTFS
/dev/sdb3            1837        2608     6201090    5  Extended
/dev/sdb5            1837        2608     6201058+  83  Linux

Partition table entries are not in disk order
```


I found how to boot back to the original boot list (where xp/ubuntu) used to be in a list. I think I must have installed ubuntu above windows xp somehow, so I have to choose the windows xp (loader) choice to choose to boot into xp. I want to get rid of this however.

Removing ubuntu 8.10 for now would probably be best for me. How can I do that without access to xp?

---

### Post by lisati on 2009-04-13
Sorry for the delay replying, I got side-tracked with doing some maintenance on one of my own machines.

It looks like you have two disk drives in your system, one with data, the other with XP and Ubuntu - is this correct?

I'm not sure exactly how to proceed and might need time to think (suggestions from other forum users would be appreciated)

---

### Post by Drumm3r4lyfe on 2009-04-13
You are correct. Is there any way I can list the windows xp choice for dual booting first? If not, then removing 8.10 would have to be done for now. If you could link me with a guide on how to do that I would be very happy :)

---

### Post by pastalavista on 2009-04-13
Now we'll need to see the output of```
gedit /boot/grub/menu.lst
```

---

### Post by Drumm3r4lyfe on 2009-04-13
Ok this is what I got for that...

```
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
# kopt=root=UUID=37c08dfa-37f5-4266-a060-f2d4758d1d05 ro

## default grub root device
```

I really need to just delete 8.10 (and install it later :)), would deleting the partition work, but is that possible without access to windows xp?

---

### Post by groovete on 2009-04-13
Hi, 
this menu.lst looks very weird for me. I don't see any boot options :confused:
Could you tell us **exactly** what you have done?
How did you delete the wubi installation of Ubuntu 8.04?
How did you install Ubuntu 8.10? Was it a Wubi installation too? 
In which system you are booting now? Is it the 8.10 installation? 
If it is the 8.10 installation, what do you see, if you open "Places / Computer" from the menu? (I tried to translate the german terms, hope it matches the english ones).

---

### Post by Drumm3r4lyfe on 2009-04-13
> **groovete said:**
> Hi, 
this menu.lst looks very weird for me. I don't see any boot options :confused:
Could you tell us **exactly** what you have done?
How did you delete the wubi installation of Ubuntu 8.04?
How did you install Ubuntu 8.10? Was it a Wubi installation too? 
In which system you are booting now? Is it the 8.10 installation? 
If it is the 8.10 installation, what do you see, if you open "Places / Computer" from the menu? (I tried to translate the german terms, hope it matches the english ones).

**How did you delete the wubi installation of Ubuntu 8.04?** I manually deleted the wuibldr and edited the boot.ini from xp.
**How did you install Ubuntu 8.10? Was it a Wubi installation too?** I burned the iso to a cd and installed 8.10 that way.
**Which system you are booting now?** Is it the 8.10 installation? Yes, but I can also boot to windows xp, but ubuntu is listed first, and I want it listed last.
**If it is the 8.10 installation, what do you see, if you open "Places / Computer" from the menu?** I see a 40 gb media (c drive I think) The cd-rom drive, My HP_PAVILLION drive ( recovery drive d ), the usb drive, and the file system.

---

### Post by groovete on 2009-04-14
OK, that's what I understood:

Your problem is just the "wrong" bootorder - beside this, everything works fine. :rolleyes:

As I understood you just deleted the wubi files. That's definitively the wrong way in a windows system. Wubi comes with an uninstaller and you should do it that way.

You should check your boot. ini, I think you edited it incorrect.

This is the boot.ini of my wife's laptop with a linux mint wubi installation as an example, booting into Windows as default option.
**You can't just copy and paste it in your boot.ini! ** Just for checking what might went wrong with your boot.ini.

```
[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Linux_Mint_Main"
```

---

### Post by Drumm3r4lyfe on 2009-04-14
Is it possible to check my boot.ini from ubuntu? As I can't get onto windows xp right now.

Is there some way I can change the boot order?

And remember I installed ubuntu 8.10 with a cd, not wubi :)

thanks.

---

### Post by groovete on 2009-04-14
> And remember I installed ubuntu 8.10 with a cd, not wubi

I remember, but there is always an option to install ubuntu like a windows program using Wubi during the installation process with the CD. In other words, Wubi is part of the Ubuntu - CD (desktop version).

What confuses me is your menu.lst. There is no entry to boot an OS. If you really installed Ubuntu seperated from your Windows installation for dualbooting there has to be one for Ubuntu and one for Windows.
In this case your boot.ini should have just the windows related entry.

You should be able to view your boot.ini from Ubuntu:

Mount this 40 gb media you talked about (just clicking on the symbol should do the trick) and have a look there. If this is your c - drive, there must be the windows files. You should see the boot.ini.

If there is a problem with the your Grub boot loader too, someone else has to help you out. I'm no expert. 

Probably it would be a good idea to search the forum for grub and / or dualbooting related threads and if you don't find a solution open a new thread with a more specific title than the one you choosed for this thread.
 

And, what means > As I can't get onto windows xp right now.
In your previous post you wrote that you are able to boot into Windows XP. Why not now???

---

### Post by pastalavista on 2009-04-14
If possible, download and burn a [SuperGrubDisk]("http://www.supergrubdisk.org/"). It can work wonders automatically...

If you still have problems, check out [this page]("http://www.supergrubdisk.org/wiki/GrubHardDiskOrder").

---

### Post by Drumm3r4lyfe on 2009-04-18
Sorry I was away for awhile.

Anyways, pastal that application is neat, but I think it just changes it so the ubuntu option to boot into is first. I need the Windows option to be first.

Is there anyway I can do that?

Thanks.

---

### Post by groovete on 2009-04-19
[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems)

---

### Post by bendib on 2009-04-19
DON'T DELETE THE PARTITION!!!! This will ruin grub, rendering your system unbootable! Here, I made you a menu.lst file. Here is what you do to install it.

1. Start ubuntu
2. remove the .txt extension from this menu.lst.txt file, so it's called menu.lst
3. hit Alt F2 and type sudo nautilus /boot/grub
4. if prompted, type your password.
5.copy your new menu.lst file to this place, after you made a backup of the old one.
6. restart, and windows should be the default. The UUID for ubuntu does not match, but it will boot anyway. Maybe throwing a fit with white text when you start ubuntu, but it will work good. This will probably disable the hibernate feature, so don't try using hibernate.
Of course windows will be untouched, and hibernate will work just fine in your windows installation.
In the event that this screws over grub, start ubuntu from the live cd, and copy your old one back. Hope this works! Ben

---

