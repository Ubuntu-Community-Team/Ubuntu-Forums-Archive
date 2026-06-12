---
title: "Why did persistent USB startup disk become corrupted?"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by yurad on 2009-04-05
I am looking  for the option to boot time to time Linux on my laptop. The best solution today would be the full Linux installation on flash drive, but so far I don't find a way how to create it on my laptop. And I try  to use Ubuntu 8.10 persistent USB startup disk. It looks very promising. I am able to install some programs,  upgrade Firefox with extensions and change the desktop environment. Everything was fine until one day it stopped to boot.There was some error during the boot. I created again the persistent disk on the same flash drive. For few weeks everything worked fine. But now  when Gnome is loading after boot I see the error message from Tomboy applet and on the top of first message I have the second message " Failed to initialize HAL". The keyboard and mouse are not responding. Ctrl-Alt-Del allows to restart. When I boot in safe mode I get the shell window. "startx" gives an error. When I try "dpkg-reconfigure hal"  I am getting something like "/var/lib/dbus ext3-fs error (device loop1)" + a lot of additional information. (Also interesting, I cannot treat this message as stderror, I mean when I redirect ".... 2> file_name" I still see the message on the screen and not in the file).
Could somebody advice what's going on with my persistent disks?  Is it possible there is a hardware glitch on my flash drive? Or is it an Ubuntu glitch with persistence of startup disk when I change the stuff on it?  BTW, what should I expect from persistent USB startup disk? And how reliable should it be?

---

### Post by Levitation on 2009-08-02
Howdy,

Happened upon your post as I was browsing the forum...

My lack of technicalese will soon become apparent, but, let me share some of my experience with USB Booting.

First off, check out [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

There is a download for a utility which can create a bootable USB (in the myriad flavors of Linux either from your own .iso or as a download). If you have a Windows OS somewhere, it actually works better. The other option, if you have Ubuntu 9.04 you can use the USB boot creator (look in System/Administration menu near the bottom). It can create a bootable USB from CD or other .iso.

It should work just like a CD, provided your BIOS is set to boot from USB. As for your USB device, they are so cheap (you can probably get a 1 GB - which is all you need for this purpose - for $5 USD) I would just get a new one and use it just for the boot files.

As your post is already 4 months old,you've probably figured this all out!

---

### Post by Mighty_Joe on 2009-08-03
There are a [couple ]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544")of [bugs ]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865") [known ]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702")with Ubuntu's Live USB Creator (the latter may be the one you encountered). 
I would consider the flash drive created with unetbootin or the usb-creator a handy way to experiment with Linux or to install it on a device that doesn't have an optical drive, but not reliable enough for every day use.
I ended up just installing Ubuntu to my flash drive.  It's faster than using the Live CD image and you can use all the space on your drive.  Have a look at my [post here]("http://ubuntuforums.org/showthread.php?t=1193680") if you are interested.

---

