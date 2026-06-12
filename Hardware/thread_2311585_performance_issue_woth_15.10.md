---
title: "performance issue woth 15.10"
date: 2016-01-28
forum: Hardware
---

### Post by zdvdla on 2016-01-28
Hi,

i just recently got a new HD and installed 15.10 but it is incredibly slow. The widows take about 3-5 seconds to appear and the text is way behind what I am typing...and I am a terrible typer.....

heres my set up:

Intel Pentium 4 3 Gz
4 GB ram
Gforce 5200
wired connection

I have tried many installs over the past 3 days and cannot get the problem solved. The closest I got was installing the LXDE on top of 15;10 and it seemed to work ok, but some of the panel buttons would not work. Namely the shutdown/restart...I tried some fixes, got it royally jacked up, installed yet again. Obviously I am not an advanced user, but it seems from what I have read that this setup should run 15 ok.
I think there is an issue with the video card (see, told ya) as well as the driver for the processor. (It was spiking 85-100 while I was just looking for answers online).
I am not gaming on this, I just wanted to use this old box for something fun and useful -- it is now the opposite of both....

---

### Post by weatherman2 on 2016-01-28
Search the dash for "additional drivers" and see if there is an additional driver you can install for that graphics card.  However, keep in mind that that's a super old, slow CPU by modern standards, so don't expect this computer ever to be very fast.

You might also try installing Gnome Flashback - gives you an old-style Gnome desktop manager:

[http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/](http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/)

(Should work in 15.10, though you will have to upgrade 15.10 soon anyway and not sure what will happen after you do.  I'd stick to 14.04 LTS myself for longer-term support.)

I use Gnome Flashback with metacity on old hardware to get decent performance.

---

### Post by mörgæs on 2016-01-29
Also worth trying Lubuntu or other lightweight distros. The 5200 deals only with simple graphics.

---

### Post by Yellow Pasque on 2016-01-29
If you really want to use the Unity interface, you'll need to install Ubuntu 14.04.1, as that's the last release that will allow the 173.xx Nvidia proprietary driver to be used (later releases use an Xserver version that the driver doesn't support).
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

---

