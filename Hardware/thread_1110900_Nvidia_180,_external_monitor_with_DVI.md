---
title: "Nvidia 180, external monitor with DVI"
date: 2009-03-30
forum: Hardware
---

### Post by lukjel on 2009-03-30
Hi!

I'm using HP Compaq 8510w with Ubuntu 8.10 64bit. It works well except one thing: external monitor. I have docking station and external monitor (the same resolution) connected via DVI port. With NVidia drivers 173 works well, with other (esp. 180) it doesn't. When I'm using VGA cable it's ok - only DVI is not working.
Any ideas?
I want to use new drivers because I've got some "shutdown" problems (it looks ACPID is hang-on and it could be a nvidia problem).

Regards
Lukjel

---

### Post by norwoods on 2009-03-30
i run two dvi monitors on a 9600gt with 180 drivers.  all i had to do is run gksu nvidia-settings 
when the nvidia gui interface is running, click X Server Display Configuration. 
click Configure...
click the TwinView radio button
click OK
set up anything you want
click Save to X Configuration File
click Quit

---

### Post by apedraza on 2009-03-30
I have the same problem with the only difference is that my system is an 8710w. The 177 drivers did not work either with the external monitor.

Nvidia X-Server Settings does not detect the external monitor. I have tried both DVI and HDMI. No luck. 

Every so often, I reload the 180 driver just to see if it has been fixed. I tried it this morning and it still does not work. Maybe this is specific to HP Compaq hardware. I had to revert back to 173 to get it working.

---

### Post by lukjel on 2009-03-30
It's even worse...

suspend is not working properly: it "goes to sleep" ok, but during wake-up screen is blank and then suddenly reboot.
Going back to 173. 

-l.

---

### Post by AlbertVeli on 2009-06-24
I have a 8710w and external monitor only works with 173.x drivers. I've tried them all, 177.x and 180.x. Both on Ubuntu and on Gentoo. It's the driver version that matters, not Xorg or something else. In 177.x and 180.x the external monitor just isn't detected.

Another problem is that 173.x drivers doesn't compile with the 2.6.30 kernel so I have to stick with an old 2.6.29 kernel.

---

### Post by CPCollin on 2009-07-29
I am running 190.18 on my 8710w and have a similar problem.

With VGA, my external monitor works fine in twinview, but via HDMI (HDMI out of laptop to DVI>HDMI converter to HDMI into the monitor) the external monitor is off center
the whole "screen" is 10% off the left side of the screen and 3% up off the top of the screen.

The whole desktop is shifted "Up" and "Left".  I do not see any controls to change the display orientation, suggestions?

---

