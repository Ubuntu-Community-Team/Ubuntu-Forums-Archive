---
title: "Drivers for my graphicscard"
date: 2008-09-27
forum: Hardware
---

### Post by Psy_Lover on 2008-09-27
Hi everyone!

I'm pretty new to linux, and idot as I am I downloaded the graphicsdrivers from ATIs webpage and Installed them.
So now the maximum ressolution on my screen is 800*600.
Can someone help me get it back to normal?
My graphicscard is an ATI Mobility Radeon X1300.
The reason I installed the drivers were that I installed Kiba-Dock and got a black field around the dock.
Please help me!


/Andy

---

### Post by WWSmith36 on 2008-09-27
Try to use displayconfig-gtk: Simple gtk tool to change xserver settings like graphics card driver or monitor.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install displayconfig-gtk
```

Then to configure your monitor resolution:

```
sudo displayconfig-gtk

```
then try to select and configure your monitor from the list or try to define your monitor by putting the inf file take from xp driver cd or floppy or from the net. If you are in trouble due low resolution and buttons are out of the screen visual try to press the ALT key on keyboard and drag the working windows to get access to buttons.

Reboot your pc.

Then go to menu System->Preferences->Screen resolution to try to get high screen resolution setup

---

### Post by Psy_Lover on 2008-09-27
Well I did as you told me, but with no luck. So I've decided to reinstall Ubuntu. I havn't got any files on it, so it's no problem.
But if I want to upgrade my drivers later, how shall I do it?
As I said, the reason I upgraded now was that there was a black box around my Kiba-Dock. And I can't change the desktopeffects either....



/andy

---

