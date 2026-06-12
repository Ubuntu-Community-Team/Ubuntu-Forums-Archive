---
title: "Advise me on purchasing a USB harddisk to boot Ubuntu from"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by pranav on 2007-04-04
In my office I work on the proprietary OS like everybody else. I have some beginner level experience with Ubuntu such as installing and using apt-get, etc. I would love to continue using Ubuntu and learn more. So i have the permission to connect an external USB hdd and run GNU-Linux thru it. I intend to use it for all practical purposes... everything dat Ubuntu is capable of handling. My questions are as follows:


1. Is it possible to install Ubuntu on an external hard disk thru a USB port?

2. If yes, will the performance be slower than a regular install on an internal hdd? I have 1GB of RAM, with a 3.0GHz CPU.

3. Which USB hdd do you recommend should i buy? Looking for around 200-300GB ?

I'm sorry for spamming if this has already been tacled somewhere else, please redirect me to the appropriate thread.

---

### Post by aysiu on 2007-04-04
1. It is *possible* but not easy. There are a lot of steps, apprently. One of these links may help you get set up:
[ Installing Ubuntu to an external USB drive - A Howto](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)
[SUCCESS - Breezy loaded on external USB drive !](http://ubuntuforums.org/showthread.php?p=436420#post436420)
[Want to install Ubuntu on external hard drive.](http://ubuntuforums.org/showthread.php?p=2370670#post2370670)

2. If you're able to set your boot loader to boot off the external hard drive, then it should be at native speeds.

3. No idea.

---

### Post by RaZer0r on 2007-04-04
well it is possibe but your bios must be able to detect the usb device as an point to boot from, so if you know thats the case, there isn't any problem about booting from that external hdd.
the speed will decrease a bit, but you won't notice the difference the difference :) so that's not to worry about eiter.
the size, well, you can put ubuntu on anything you want actualy :)
200-300 is a overkill if you only want the os and some drivers to be installed but it's allway's great to have some music/movies on the external drive too (if you boot more into windows then linux i'd say to use ntfs or fat32 (preferably fat32 cause ntfs isn't supported out of the box)
so format your extenal disk like this:
10gig /
20gig /home
2 gig swap
rest fat32
any usbdisk should work fine, i personaly use an box to make an ordinairy hd to an usb device (external enclosure) cause i used to put the drive in and out my desktop all the time...
you might as well consider using ext3 as filesystem for the rest partition, but you'll need some drivers for windows to be able to read and write to it, and my work didn't allow me to install drivers on the desktop i'm using.. so i managed to do it otherwise and still have the read/write support for both os's

hope i have been of any help to make your choice

---

### Post by pranav on 2007-04-04
Thank you for replying.

You guys have clearly understood my situation. I restarted my PC and checked the Boot Sequence... It is set to 1.CD-ROM 2. USB Device 3.Hard Disk Drive

So yes, this machine will be capable of booting from the USB drive.


I totally understand  that 200+ GB is an overkill for Ubuntu. What I intend to do is boot a couple of distros of GNU-Linux off the external drive... both rpm as well as deb based... for educational pursuits.

I really like the idea of a regular Hd being converted to USB drive using a case. Makes a lot of sense . I just need to be sure that the hardware that i purchase should be supported by Ubuntu, otherwise I shall get stuck.

Any inputs on what kind of casing or boxes are supported by Ubuntu out of the box... any list or resource where I can get the info ?

---

### Post by eentonig on 2007-04-04
I was unable to tamper with the main HDI currently run from a 80G Western Digital.

The first howto is the one I followed. It's not that difficult, but you must keep your head to it. Pay attention to the partitioning part and to the grub installation and configuration.

---

### Post by pranav on 2007-04-06
I got a Seagate 250 GB hdd. Put it in a cheap casing (ide to usb)

Also i set the boot sequence to USB drive first.

Then I installed Linux and installed the bootloader on the external hdd.

Now i restart and it directly boots up Windows...

Is the drive bootable ? Did i end up getting the wrong kind of casing ? or did i make a mistake in installing GRUB ?

---

### Post by eentonig on 2007-04-06
Probably, the USB drive is not bootable. Or you missed somethin in the BIOS.

Check BIOS again to see IF the USB HD is set as the first boot device. And pay attention, as in my BIOS, I have several USB boot options (HD, Flash, CDROM, ...) and it only worked after I set it to the correct value.

I actually only found this by forcing my BIOS to show me a boot option menu (like GRUB does).

---

### Post by pranav on 2007-04-06
The only option it gives me is USB Device... no other detailed options... however a friend had a bootable usb stick (1GB only)... this worked.

So it means BIOS is certainly letting USB devices to boot.

I'll try reinstalling and if that doesnt work then it means i got the wrong casing!

---

### Post by eentonig on 2007-04-06
Actually, wait before reïnstalling.

Try booting it from another PC. To see if it's not BIOS related. As said in my previous post. It(s not because your BIOS has a USB boot option, that it support USB Harddrives.

---

### Post by pranav on 2007-04-06
Now i installed the GRUB on the BMR of the internal harddisk and then tried booting...

It started n within 2 secs it read Kernel Panic n it just froze forever!

---

### Post by pxwpxw on 2007-04-06
> **pranav said:**
> Now i installed the GRUB on the BMR of the internal harddisk and then tried booting...

It started n within 2 secs it read Kernel Panic n it just froze forever!

**pranav**

You may need to see this Howto, there are a few tricks to get the correct boot configuration.
I dont think its a problem with your external usb drive hardware, just the boot config.

[http://ubuntuforums.org/showthread.php?t=308027](http://ubuntuforums.org/showthread.php?t=308027)

 Ubuntu Forums > Ubuntu Release Assistance  > Other Support Categories  > Tutorials & Tips

How to install Ubuntu Edgy to USB, to boot from any USB bootable machine

---

