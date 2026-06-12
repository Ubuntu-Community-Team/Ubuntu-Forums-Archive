---
title: "booting from a usb to install Ubuntu - Voting for downloadable flashmemory version?"
date: 2008-10-18
forum: General Help
---

### Post by AndEat on 2008-10-18
I've been searching and wading through web pages to do one thing:

1. place an Ubuntu .iso (or some form) on to a flash memory drive 

2. boot from this flash drive 

3. install Ubuntu 

that is it. I don't want to mess with 1000 different files, I don't want a live usb, I don't want to waste the time I've wasted to attempt to get this accomplished. 

What I tried here: 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

did NOT work for me. I'm not sure what wrong turns I took. Unetbootin is just perplexing and unclear for the time I spent going over and trying to use it, I don't want to mess with a cd or liveusb at all and skipped over the second. Manually, I tried several times, several configurations, nothing. I'm willing to accept I didn't do something in the correct manner, but didn't have the time to mess with it. 

This (below) did work for a copy of Arch Linux, although I didn't go through with the complete install, it copied easily and booted smooth, no problems:

*****************
USB stick

WARNING: This will destroy all data on your USB stick.

Insert an empty or expendable USB stick, determine its path, and dump the .img to the USB stick with the /bin/dd program:

dd if=archlinux-2008.06-[core_or_ftp]-i686.img of=/dev/sdx

where if= is the path to the img file and of= is your USB device. Make sure to use /dev/sdx and not /dev/sdx1.

Check md5sum (optional):

Make a note of the number of records (blocks) read in and written out, then perform the following check:

dd if=/dev/sdx count=number_of_records status=noxfer | md5sum

The md5sum returned should match the md5sum of the downloaded archlinux image file; they both should match the md5sum of the image as listed in the md5sums file in the mirror distribution site.

Continue with Boot Arch Linux Installer 
****************

I haven't tried this with Ubuntu,maybe it would work? That's what I want - copy an image or iso to a memory drive, boot and install. I do not want to waste an afternoon trying things that 'might' work. I want to move away from using cds/dvds totally and completely. 

So I'm prepared to rant a bit unreasonably but wanted to ask if there is a method or quick tut for getting a bootable install (pref alternate install) onto a flash drive? If i were more savvy and had the time I do it and put it up for download myself. 

so the point of my post....

Is there a place to petition for a downloadable, easily burned/copied version of Ubuntu to install to a computer without a cd?  With the rise in netbook sales, I'd think this will become requisite. I'm a long time Ubuntu user for my personal machines, and in general prefer to do things the smart, quick way rather than beat my head against a wall. 

Any thoughts?

---

### Post by AndEat on 2008-10-18
various resources 

[http://stickytapesolutions.com/imageForStick.html](http://stickytapesolutions.com/imageForStick.html)
[http://www.debian.org/releases/stable/i386/ch04s04.html.en](http://www.debian.org/releases/stable/i386/ch04s04.html.en)

---

### Post by AndEat on 2008-10-24
still looking for a satisfactory answer? more resources:

[https://help.ubuntu.com/community/Installation/FromCForUSBStick](https://help.ubuntu.com/community/Installation/FromCForUSBStick)
[http://wiki.soekris.info/Installing_Ubuntu_7.04_Server_via_debootstrap](http://wiki.soekris.info/Installing_Ubuntu_7.04_Server_via_debootstrap)
[https://wiki.kubuntu.org/DebootstrapChroot](https://wiki.kubuntu.org/DebootstrapChroot)
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by jerome1232 on 2008-10-24
There is this new entry in my menu under 8.10 perhaps it's what your looking for. It allows me to create a bootable usb disk from a cd, or iso file. My usb stick is  too small :( The program is called usb-creator

I don't know if it's in hardy repo's or not, seem's like it's only intended to work with Ubuntu iso's.

```
Package: usb-creator
Priority: optional
Section: admin
Installed-Size: 192
Maintainer: Evan Dandrea <evand@ubuntu.com>
Architecture: all
Version: 0.1.9
Depends: python, python-central (>= 0.6.7), python-gtk2, python-glade2, python-dbus, syslinux, parted
Filename: pool/main/u/usb-creator/usb-creator_0.1.9_all.deb
Size: 21122
MD5sum: aac6453dde7e57ee376f645f44fd1489
SHA1: f4f9d16dd428e9c177426b26878318caa4744ad4
SHA256: 984a4cc044d43f1f86add0580feac56b75cfb25555a022f39070e9a1fc5fe912
Description: Ubuntu USB desktop image creator
 This is a simple utility designed to make bootable USB desktop images from
 Ubuntu CDs.
Python-Version: current
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop
```

---

### Post by C.S.Cameron on 2008-10-24
Unibootin, usb-creator and liveusb will all make bootable flash drives that you can install from.
Unibootin works within Windows and has a Ubuntu version.
Usb-creator is included on the Live CD under System.
Both will build your stick in under 5 minutes.

---

