---
title: "USB gamepad not working"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by Randabis on 2004-12-26
Hello, just installed ubuntu and I must say, you truly DO never go back. This is the best debian-based distro I've ever used. :)

Anyhow, I'm having a problem with my USB gamepad. It is an AxisPadFX from Gemini Industries Inc. 

The pad is supported in Linux, I know this because I've had it running in both Norton Linux Desktop and Suse 9.1 (with 2.6.7 kernel I believe), but I cannot get it working in ubuntu. 

The pad is detected, and shows up in device manager, but I can't get it to work with any programs (tried ZSNES and VBA so far).

Anyone have any ideas out there? It'd be a shame to have to boot into Windows 2k to do some light emulation gaming. :(

---

### Post by Randabis on 2004-12-26
I fixed it guys. :)

I had to do a couple of things.

First, 

sudo apt-get install joystick

then

sudo apt-get install jscalibrator

and finally,

sudo chmod 666 /dev/input/js0

Now it works. Thanks anyway, I'll continue enjoying my new favorite distro now. :)

---

### Post by October on 2005-01-05
Thanks for posting the way you did it!  That worked awesome!

I have a Saitek USB Cyborg Gold joystick that I was I afraid I might have to throw away...  now I can fly planes again in Battlefield 1942 :D

---

### Post by Cresho on 2007-04-25
this post saved my saitek cyborg 3d gold usb

---

