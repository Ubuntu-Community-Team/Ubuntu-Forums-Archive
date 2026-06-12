---
title: "Input Problems (Wacom Bamboo Pen, Wireless Mouse, and touchpad)"
date: 2010-06-20
forum: Hardware
---

### Post by Thryn on 2010-06-20
EDIT: This is solved. Feel free to delete this thread, or ignore it.

I was going to post this in one of the Wacom threads, but since I just noticed another couple of problems that may or may not be related.

Yesterday I set up my tablet (Wacom Bamboo Pen) [using this guide (except with the most recent version of linuxwacom - 0.8.8-3]("http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-lucid-lynx-and-wacom-bamboo-ctl460/")) and it worked fine, including pressure, once I adjusted the settings in GIMP properly (before all that the tablet didn't do anything). I also added a few lines to the configuration file, as detailed [here]("https://help.ubuntu.com/community/Wacom"). It did say at one point during the setup that I should get xf-iput-wacom but that I could still compile the kernel, which I did. And since the tablet worked fine at the time, I didn't worry about it until later.

But I powered down the computer for the night, and when I tried the tablet this afternoon, it didn't do anything! Bizarrely, it doesn't work properly under Windows 7 either - there it functions as a mouse (relative mode?) and I am unable to change the settings. But in Ubuntu it does nothing whatsoever.

Oddly enough, I can't right click in Firefox, either with my wireless mouse or with my laptop's touchpad.

The reason I think this might be connected is that last night I was fiddling around trying to get my touchpad to turn off when I plugged in the mouse. This involved fiddling with xorg.conf and another file, but in both cases the file was initially empty and I deleted the added lines when they didn't have the desired effect.

By the way, I'm running Lucid netbook edition (with the Kubuntu desktop package on top, but I did all this on GNOME) on an ASUS UL30a series. If you need more info please ask, and please go easy on me because all of this stuff is way over my head. Which is probably how I get in this mess in the first place.

EDIT: Oddly enough I can now right click. The tablet is still out of commission though.

EDIT2: Solved it myself by adding 'wacom' to /etc/modules. Now it works fine again. Sorry about the panic - I got bit by the learning curve. I'm sure I'll be back for more help later.

---

