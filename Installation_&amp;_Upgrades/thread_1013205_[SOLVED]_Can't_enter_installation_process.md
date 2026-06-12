---
title: "[SOLVED] Can't enter installation process"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by vikkevest on 2008-12-16
Hello, I have recently bought a new computer and is trying to install ubuntu. I have never isntalled ubuntu on this particular computer so its gotta be something with it.

When I try to enter the installation process (choose install ubuntu in menu) the system loads (the graphical loader) and then everything just goes black and nothing happens.

I have tried ubuntu 8.04 kubuntu/ubuntu and 8.10 kubuntu/ubuntu and the same thing happens everytime. I have used CD's that have worked before and the 8.10 CD is ordered from canoncial (so I guess it should work?)

Im using:

Intel core 2 duo
Geforce 9600GT
Intel P35 Gigabyte

Its no special or advanced hardware so im suprised that it doesent work.

I have WinXP and Arch Linux already installed.

Could anyone point me in the right direction? :confused:

---

### Post by Pumalite on 2008-12-16
Have you been able to boot the Live CD and get to the Desktop?
If not; you might need the Alternate CD.

---

### Post by vikkevest on 2008-12-17
No I can't enter the installation, can't seem to enter the desktop environment. It just gets black after the graphical loader is finished.

I have now installed ubuntu on my hdd using the alternative cd. But the same thing happens: When the graphical loader is done everything gets black and nothing else happens.

This there anyway to get a errorlog or something?

Has anyone else ever encountered this problem with ubuntu?? :confused::confused:

---

### Post by vikkevest on 2008-12-17
Okay Its seems like this guy [http://ubuntuforums.org/showthread.php?t=1011226]("http://ubuntuforums.org/showthread.php?t=1011226") has the same problem so im moving my questions there. Must be the monitor.

EDIT: I have now located the problem. I have 2 DVI ports on my graphiccard. They were connected like the following:

- One DVI-DVI cable connected from the DVI port on the monitor to one port on the graphiccard.

- One HDMI-HDMI(with DVI converter) cable connected from the TV to the graphiccard.

If I have either of these connected ubuntu wont show on the monitor.

The only way to get i to work was to connect a VGA-VGA(DVI converter) cable from the VGA port on the monitor to the DVI port on the graphiccard. This solution didnt work if I had the HDMI cable connected to the graphiccard.

Summary: It doesent seem to like DVI.

When I was able to enter ubuntu I enabled nvidia drivers and did a nvidia-xconfig then I could have both cables connected to the graphiccard, even dualscreen worked nicely :) . Maybe the problem lies in xorg.conf?

---

