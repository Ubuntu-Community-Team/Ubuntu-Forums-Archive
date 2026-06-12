---
title: "ATI Mach64 GX - Will It Work?"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by zerhacke on 2005-08-15
My nVidia Geforce 2 MX 440 blew up.  I had to replace it.  All I could get ahold of was an ATI Mach64 GX card - old, but it works.  Before you say it, I cannot replace the card with something more current.  I am disabled and live on a very strict budget.  It will take me 6 months to raise the money for a 50 dollar card.  Replacing the card with something more current is simply not an option.

Will the ATI Mach64 GX work in Ubuntu 5.04?  I reinstalled Windows thinking that it was a Windows problem before I figured out that the card was blown and accidentally reinstalled Windows on the Ubuntu drive  (I have three drives in my computer - windows, data, and ubuntu).  Now I have to reinstall Ubuntu, but I don't want to do it untill I am sure that the ATI card will work.  My baseline requirements to consider it working are the capability to do 1024X768 at 16bit color depth, which is what it will do in Windows.  I suppose 800X600 would be passable, but I really want it to do 1024X768.

Will it work?

---

### Post by zerhacke on 2005-08-16
Bump

---

### Post by zerhacke on 2005-08-16
After a giant nightmare, I have an answer.

Will it work?  Sort of.  You have to be willing to work for it and make some sacrifices along the way.

After not getting a reply here from anyone (oh, and thanks for that ever so much, it really gives me that community spirit to see so much help being offered.  Really.), I decided to try it and see if it will work on my own.  I installed, ran through the setting up, and Ubuntu prepared to launch the X server.

It failed, which is no gigantic surprised.  Examining the output showed me that this card cannot do 24 bit color depth.  Again, no surprise, as Windows won't do 1024X768 at 24 bit color either.  So I prepared to edit the xorg.conf file and Lo and Behold, there's no command line text editors that I am aware of on Ubuntu with the default install.

So I sudo apt-get install tex.  It installs.  I find that I cannot figure out how to use tex.  I never was very good at command line editing anyways.  So I come up with another approach.

I have a working Windows installation.  It's a trivial thing to mount a Linux partition on Windows using ext2fsd.  I mount up in Windows, copy the xorg.conf file to my C: drive, edit it to have a default of 16 bit color instead, and reboot.

In Linux again, I create a directory and mount my Windows C: drive to the directory.  A quick sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup and then sudo cp /mnt/hda/xorg.conf /etc/X11/xorg.conf and I'm up again.  Or so I think.

Turns out the card can't do 16 bit color at 1024X768 either.  So I redo the whole situation, this time making it display in 8 bit color as default, and retry.

I have X.  It really... REALLY sucks on this video card.  I feel like I'm back in the days of running Windows 3.11 on top of DOS.

Oh well, if I want it to look pretty I can always boot to Windows.

I have only one question through all of this though.  Anyone know if this card would do 15 bit color instead of just 8?

---

