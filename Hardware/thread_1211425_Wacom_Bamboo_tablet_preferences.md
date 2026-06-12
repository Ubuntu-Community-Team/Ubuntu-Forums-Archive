---
title: "Wacom Bamboo tablet preferences"
date: 2009-07-12
forum: Hardware
---

### Post by Estroyer on 2009-07-12
I have just installed the Wacom packages through the Synaptic Package Manager and this is what it says now:

I see the following text under "Wacom Tools" :

This package provides utilities to test and configure Wacom graphics tablets.
You will need kernel and X.Org driver support for your tablet to use them.


And under Xserver-Xorg......  I get to see:

This package provides the X.Org driver and udev support for Wacom tablet
devices.

Note that it is not a part of the X.Org distribution since X11R6: this driver
is from the linuxwacom project. See [http://linuxwacom.sf.net](http://linuxwacom.sf.net) for details.

You will also require a kernel module which supports your tablet. Many types
are supported by the 'wacom' module supplied with current Linux kernels. If
yours is not one of them (yet) then see the wacom-kernel-source package for
the most up to date module available.

----------------
If I understand it correctly, I need a kernel to make use of this?
Well, as I am familiar with my PSP kernels ( who needs a DS???), so I know a little what it's saying but what kind of kernel should I get and where can I find them/it?
EDIT
I was clever to click on the link provided (duh) I'll read through that site a bit more in order to figure it out. If I succeed I will post it here...if not...I will also let it be known ;-)

---

### Post by Favux on 2009-07-12
Hi Estroyer,

The kernel module they are talking about is for the usb from your tablet and is called wacom.ko.  It should have been installed in the kernel-images when you installed.

To see if it is in place in a terminal:
```
dmesg | grep [Ww]acom
```

You should run those list commands and then we can move on saving you some time.

---

### Post by A. J. Rimmer on 2009-07-12
Which version of Ubuntu are you running?

I have a Wacom Bamboo which did not work "out of the box" with Gutsy (8.10), but which works very well with Jaunty (9.04) without installing anything else.  The only thing that does not seem to be supported in pressure-sensitive brush strokes and the "eraser" function on the pen.

I was not aware of the wacom-tools package; I will have to give it a try and see what it does.

By the way, looking at the package manager, I see that xserver-xorg-input-wacom is installed by default in Jaunty.

Hope this helps ... bottom line is that you may already have everything you need.  If not, an upgrade to Jaunty might be the easiest path.

---

### Post by Favux on 2009-07-12
Hi Estroyer and A. J. Rimmer,

A. J. pressure and eraser are both supported.  Sorry Estroyer about repeating myself.  Here goes:

Wacom-tools has wacomcpl among other things.  And A.J. that's the configuration and calibration gui for Wacom.

What I'm about to tell you to do has worked for a bunch of Bamboo users.

First the default 10-wacom.fdi is not parsing the device names correctly and that's why wacomcpl doesn't work.  To see this enter in a terminal:
```
xsetwacom list
```
That should return the linuxwacom names like stylus, eraser, cursor, and pad.  If it is blank that's why wacomcpl won't work.  To see what names HAL is returning enter:
```
xinput --list
```
To fix this do the following.

First you will need to change the 10-wacom.fdi to one that does parse the names correctly.  So go to post #176 (this is Loic2's Wacom wiki forum thread) here and follow the directions:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Then to set up wacomcpl in Jaunty see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

For additional info. on how to set up the Bamboo (the pad) see shatterblast's post #188 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=19](http://ubuntuforums.org/showthread.php?t=967147&page=19)

And then to set up Gimp look at the Wacom wiki near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

That should get you both set up.  Good luck!

---

### Post by A. J. Rimmer on 2009-07-12
Favux --

Thanks very much! Just trying to help a guy out and here I get some good info myself.

I'll have to dig into this when I get a chance this week and see what I can accomplish.

---

### Post by Favux on 2009-07-12
Hi A. J. Rimmer,

You're welcome.  I hope it helps you get things set up the way you want them.

---

### Post by A. J. Rimmer on 2009-07-12
Favux --

A big THANK YOU!

I installed wacom-tools but I don't know if I really needed to or not.  

The one bit of information I was really missing was the Wacom Community Documentation page.  After looking at that and going into the Gimp setup, my pen pressure and eraser functions work as desired.

Haven't made much use of my tablet lately, guess it is time to get it out again and do something with it!

---

