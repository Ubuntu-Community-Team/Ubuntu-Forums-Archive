---
title: "how do I connect an external monitor to my laptop?"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by negativ on 2007-07-03
This seems like the simplest thing in the world and it irritates me that this doesn't work.

I have Feisty on my laptop, an old-ish Dell with a GeForce4 440 Go and the accelerated nvidia drivers.

How do you make Ubuntu aware of the external monitor?  I have video from it during the BIOS messages at boot, but as soon as X should load it goes black.  

I'm sure it's all X config, but I went through *dpkg-reconfigure xserver-xorg* and all I managed to do there was make the GUI unusable until I reverted to the previous config files.

How can I make this work?  The native res of the laptop LCD is 1400x1050, and I want to run the external monitor at 1280x1024.

In Windows this amounts to maybe 4 mouse clicks.

EDIT:  Note that I'm not looking for a seperate desktop on each monitor or anything fancy like that.  I just want the stuff displayed on the LCD to be displayed on the CRT, not necessarily at the same resolution.

---

### Post by aquavitae on 2007-07-03
I thought you could set this up under system settings.  I seem to remember there's an option for multihead, and then its just a matter of clicking.  Not at my Ubuntu PC now so I can't check.  I know there's a GUI tool for it in Kde - are you using Ubuntu or Kubuntu?
> **negativ said:**
> In Windows this amounts to maybe 4 mouse clicks.
Not usually - Last time I tried this on windows it took me an hour of tring to find the right buttons to click and numerous restarts.  When I finally got it working it had a wrong resolution.  Last time I did this in linux (same hardware) it took me 30 seconds using kconrol (under kde).  I guess it depends how well supported the hardware is in each system

---

### Post by negativ on 2007-07-03
it's Gnome - can't stand KDE.

---

