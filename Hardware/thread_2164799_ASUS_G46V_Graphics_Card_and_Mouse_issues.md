---
title: "ASUS G46V Graphics Card and Mouse issues"
date: 2013-08-01
forum: Hardware
---

### Post by mathieu-mgkgroup on 2013-08-01
Hi all,

I've been using ubuntu since 7.04 and I have never had any issues with it hardware-wise, until I got my new laptop. I recently purchased an ASUS G46V after my house was broken into and refused to get to know windows 8; after a few failed attempts to install ubuntu 13.04 (I would install graphics card drivers and it would essentially break everything to the point where it wouldn't even boot) I fainlyl got 12.04 working. But since then a few issues are nagging at me that I'd like resolved.

Firstly, and probably the most annoying is the mouse. It has a touchpad mouse and it registers it as a generic ps/2 mouse. Though the touchpad works, the nice two-finger/edge scrolling features don't work, which really I've gotten used to just using my arrow keys, but I'd still like it fixed (I have the capability, might as well take advantage of it). I've already followed along with document section with this and there's no luck. I did see there was this whole manual way to remove and reinstall it, but it looked scary and after having to reinstall the whole OS several times I didn't want to break it all again. I also posted a question [here](http://askubuntu.com/questions/317533/ubuntu-12-04-touchpad-menu-gone) but without much luck.

Secondly, my grpahics card. This is what caused all my hurt in the beginning, because every time I installed the restricted drivers for it, it would break everything to the point of it either a) not booting or b) the window manager being gone. It's an NVIDIA GeForce GTX, which is odd because I've owned several computers over the years, almost all with nvidia graphics cards and never any issues with them. I'm not much of a gamer, but I did buy a gaming laptop and it would be nice to put it to use and test its limits. I've followed a few guides with no luck, and I'm almost afraid to touch it again and break everything.

**tl;dr** My touchpad doesn't work, my nvidia GeForce GTX graphics card doesn't work.

Thanks so much!

---

### Post by Petro Dawg on 2013-08-01
I'm not much help with graphics cards, but have you tried getting the touch pad to work correctly using dconf?

The following link may or may not be helpful...
[URL="http://www.upubuntu.com/2011/11/is-your-laptop-touchpad-not-working.html"]
http://www.upubuntu.com/2011/11/is-your-laptop-touchpad-not-working.html[/URL]

Back before my laptop died my solution the touch-pad problem was to use the "touchpad-indicator" program and set it to disable touch pad when external mouse was plugged in.  Most of the time I preferred using a wireless mouse rather than the touch-pad anyways.

Hopefully the program is still supported, try the following link for instructions to download and use if you are interested in that solution...

[http://www.addictivetips.com/ubuntu-linux-tips/automatically-disable-touchpad-when-mouse-is-connected-ubuntu/](http://www.addictivetips.com/ubuntu-linux-tips/automatically-disable-touchpad-when-mouse-is-connected-ubuntu/)

---

### Post by pqwoerituytrueiwoq on 2013-08-01
[http://i.imgur.com/EG6zyWQ.jpg](http://i.imgur.com/EG6zyWQ.jpg) that your issue on raring?
if so reboot a few times it should work eventually, once you upgrade the kernel to the [latest 3.9 series]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.11-saucy/") it should be fine

as for the mouse [FONT=courier new]lsusb[/FONT] output?

---

### Post by mathieu-mgkgroup on 2013-08-01
Petro:

I followed the first article, but the issue isn't that the mouse is disabled, it's that it doesn't see it as my default mouse.. I guess. When I open the menu for mouse and touchpad, it doesn't even have a touchpad menu anymore. I don't know what changed, because for the first few days it worked just fine

pqwo:

No, it wouldn't display anything. Some reboots I would just get a purple screen (no ubuntu logo or anything, just a blank purple screen) and some reboots I would get a black screen. Every 1 in 10 or so it would get to the login screen, I could log in and the window manager was broken, and even purge-removing the drivers didn't fix it; however, I don't think I tried upgrading the kernel (I though 13.04 came with the upgraded kernel)

as for my lsusb output:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 09e8:0073 AKAI  Professional M.I. Corp. 
Bus 003 Device 003: ID 08bb:29b0 Texas Instruments Japan PCM2900B Audio CODEC
Bus 001 Device 004: ID 13d3:5188 IMC Networks

---

### Post by pqwoerituytrueiwoq on 2013-08-01
i will point out that 12.04 may be too old for your gpu
if you can't get raring (13.04) to boot does saucy (13.10) boot (saucy is under development and it not yet complete and is subject to lots of things breaking at this stage)

---

### Post by mathieu-mgkgroup on 2013-08-01
well raring would boot until I installed the graphics drivers; I haven't tried saucy (mostly because I'm not a developer/don't have the know-how to fix broken things)

---

### Post by pqwoerituytrueiwoq on 2013-08-02
you have you ubuntu since 7.04 and don't know how to fix anything?
before installing nvidia in raring install the mainline kernel
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)
just replace this command
[FONT=courier new]KernelUpdateChecker -no-rc[/FONT]
with this command
[FONT=courier new]KernelUpdateChecker -v 3.9 -r saucy[/FONT]
was that picture i posted earlier what happened when you installed the driver?

---

### Post by mathieu-mgkgroup on 2013-08-02
Well, if something goes horribly wrong I'm not a linux expert on fixing it, especially when it comes to hardware issues. 

I'll follow these instructions and hope I don't break my laptop again :P thanks so much for your help!

Before installing raring, though, should I do a fresh install, or would it work to just upgrade it with the update manager? Just need to know if I need to back everything up or not.

And no to the picture; it would either be a purple screen by itself (no ubuntu logo or anything) or it would be a black screen with no text, every once in awhile it would boot to the login page and the window manager would be broken, but even after a purge-remove it didn't fix.

---

### Post by pqwoerituytrueiwoq on 2013-08-02
may want to try the xorg edgers ppa

this thing does not use hybrid graphics does it?

---

### Post by mathieu-mgkgroup on 2013-08-02
to be honest I have no idea, sorry

---

### Post by pqwoerituytrueiwoq on 2013-08-03
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
it is known as NVidiaOptimus if you have that you should look at the bumblebee project

---

### Post by mathieu-mgkgroup on 2013-08-03
I don't believe it is, it's just an nvidia GeFore GTX

---

