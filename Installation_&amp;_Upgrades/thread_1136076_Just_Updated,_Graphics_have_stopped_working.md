---
title: "Just Updated, Graphics have stopped working"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Mindbleed on 2009-04-24
I have just updated to 9.04 from 8.10.  The update went fine, but then when I booted, the boot failed after it gave the Ubuntu loading screen.

It showed a screen with strange colors and white and black lines all over the screen and generally did not work.

I have had graphics problems in the past, but have had them all worked out, I just could not use the Restricted drivers or else this would happen.  Whenever this happend, Ubuntu would revert to Reduced-graphics mode and everything would be fine, I just needed to run a script from one of my logins.

However, I now cannot even log in, so I do not know what to do.  I can boot to terminal which I am doing now (Using Links2 as a browser).  I do not know how to reset my graphics from this though.

Any help would be much appreciated

---

### Post by psmar on 2009-04-24
hit escape at the beginning of grub then choose the recovery mode, a box with options should show up and near the bottom is an option to fix the xserver ( shouldset your video right, ( at least it worked for me)

---

### Post by cljbville on 2009-04-24
I have an IBM Thinkpad R51 with an ATI Mobile Radeon card. After my upgrade to Jaunty, xorg messed up big time. However I got lucky and found a solution! :razz:

After messing around with trying to enable graphic effects on previous versions I came to the conclusion the flgrx driver was no good for me. I checked my laptop after the Jaunty upgrade and found the xorg-driver-flgrx package was back. So even though it wasn't referenced in my xorg.conf I took it out and it works fine now.

When the laptop was booting I hit ESC and went in to the recovery option. On the menu I selected the root shell. I then removed the xorg-driver-flgrx. Now I can get in fine just like before the upgrade! I've never been able to get the 3D graphics to work on any version, but it still looks great even with out the effects. 

Here's the command to remove the flgrx driver:  "apt-get remove xorg-driver-flgrx"

Here's my xorg.conf file too, I left out all the comments to keep it short:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by MeanStreak on 2009-04-24
I have exactly the same graphics problem - could you please explain in more detail how I "remove the xorg-driver-flgrx"?

I tried running "apt-get remove xorg-driver-flgrx" however it couldn't find the xorg-driver-flgrx' package. This is really frustrating, I've got to get on with some work!

---

### Post by Mindbleed on 2009-04-24
> **MeanStreak said:**
> I have exactly the same graphics problem - could you please explain in more detail how I "remove the xorg-driver-flgrx"?

I tried running "apt-get remove xorg-driver-flgrx" however it couldn't find the xorg-driver-flgrx' package. This is really frustrating, I've got to get on with some work!

It is xorg-driver-fglrx  (the g and l are switched)

This has completely fixed my problem, thank you so much.

---

### Post by MeanStreak on 2009-04-24
Thanks! It's working now. I booted into Recovery Mode, selected the command line option and ran the following command:
```
apt-get remove xorg-driver-fglrx
```

Rebooted as normal and can now login. Phew.

---

