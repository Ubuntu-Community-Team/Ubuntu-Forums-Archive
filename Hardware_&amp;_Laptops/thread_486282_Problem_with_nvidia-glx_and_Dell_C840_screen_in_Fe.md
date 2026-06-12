---
title: "Problem with nvidia-glx and Dell C840 screen in Feisty"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by eimajenthat on 2007-06-27
Greetings-
I have just installed the nvidia-glx package on my Ubuntu 7.04 Feisty installation.  Previously, I was using the generic nv driver.  With a couple modifications to xorg.conf, I was able to get X to start with the nvidia driver.  However, this display is somewhat abnormal.

The screen on this laptop is 15" and supports up to 1600x1200 resolution (at least with the nv driver).  However, the nvidia driver seems to think the monitor is only 1400x1050.  In Gnome preferences, this is my max resolution.  The big problem, however, is this.  The desktop is only displayed on part of the screen.  About 1.5 inches on the right side is consumed by colored lines, and about 1.2 inches on the bottom is consumed a repeat of the top of the desktop.

Everything worked fine with NV, except for GLX.  I only changed the driver, and the line about using DFP (without that, I get a blank screen).

What is causing this and how do I fix it?

Thanks a bunch!






Here's my xorg.conf: [http://pastey.net/69978](http://pastey.net/69978)

It looks like this:
[IMG]http://farm2.static.flickr.com/1350/643350026_14ce7db20b_o_d.jpg[/IMG]

---

### Post by eeyore76 on 2007-07-04
I'm having the same problem on an old Dell laptop. Have you solved the problem yet?

---

### Post by fnandocc on 2007-07-21
Using the nvidia-glx from the repositories.

Writing this using the same laptop Dell C840
Try this xorg.conf

[http://pastey.net/71135](http://pastey.net/71135)

If This doesn't work check the problems sections in this Nvidia How To

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

---

### Post by TravMan63 on 2007-08-02
I tried the above - (on Dell C840 - Nvidia Geforce4 440 Go 32 MB) - and it shutdown my X server.

Removed nvidia driver - n/c

Replace xorg - will update
-----
Tried both xorg files - neither one works for my Dell - shut down x server

at one point the (X11) error of kernel and driver having mismatched versions did appear

----
actually - I had success when I did this:
dpkg-reconfigure -phigh xserver-xorg

(after sudo apt-get --purge remove nividia-glx
and wading thru this page ->   [ http://doc.gwos.org/index.php/Latest_nvidia_feisty ]( http://doc.gwos.org/index.php/Latest_nvidia_feisty )  )

---
edit - install comments
When I last installed Ubuntu CE 7.04 on this machine, I was attached to an external monitor; the attached screen was broken - I replaced the laptop screen later (same day) and  the res was limited to 800x600 or 640x480 on the laptop screen, I think the external was 1024x768 max.  The max now is 1600x1200.  I would note that videos played at this resolution and Impress presentations are slower/chopier than at 1024x768 or 800x600.

I think - on the 1st install - when the laptop screen was working - the resolution was fine.

Summary - it may depend on what active video screen is present when installing as to what video driver/setup is installed (although I would think that it would look at the video card.  Perhaps the updates (in update manager) corrected that?)


TM

---
edit - external monitor with config change.
I found out - that with this configuation - that works fine on the LCD - does not work AT ALL on the external port.
(The output on the external video port is fine until X starts, then it 'goes funky' with flashing orange etc... it made no difference trying either kernel, booting with external monitor plugged in or not, internal disabled etc...)

I went to use this for an Impress presentation and...

Be fore-warned.

TM
--
edit - logout garbage
also with this config (when going from 800x600 res desktop to 1600x1200 log on)
the log on screen can become garbled - just ctrl alt backspace

---

### Post by irotas on 2007-12-16
> **eimajenthat said:**
> About 1.5 inches on the right side is consumed by colored lines, and about 1.2 inches on the bottom is consumed a repeat of the top of the desktop.

I had this exact same problem (on the same laptop, even). After many unsuccessful attempts, I finally found something that worked:
[http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26](http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26)

Hope that helps somebody in the future! :)

-Adam

---

### Post by eeyore76 on 2007-12-17
Hi

I found this, and it helped me! 

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/33075](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/33075)

---

