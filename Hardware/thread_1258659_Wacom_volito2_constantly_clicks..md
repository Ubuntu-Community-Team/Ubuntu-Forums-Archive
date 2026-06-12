---
title: "Wacom volito2 constantly clicks."
date: 2009-09-05
forum: Hardware
---

### Post by theCroc on 2009-09-05
I'm having a strange issue with my Wacom Volito2 tablet in jaunty. When I plug in my tablet it is recognised but only the main cursor works and it is constantly acting like it's clicking. I can hover the pen over the pad and it clicks anything it hovers above on the screen. I've replaced the .fdi file with Favux version so now it parses the device names correctly. It still does not react to the eraser and it constantly acts like a mouse with the left mouse button held down. 

Any ideas what I can do about that? 

I'm using UNR with the standard linuxwacom packages.

---

### Post by Favux on 2009-09-05
Hi theCroc,

By any chance did you also add a custom_wacom.fdi?

Did you go on to use 'wacomcpl' to configure your tablet?  It's the LWP's calibration and configuration gui.  If you have "wacom-tools" installed (through Synaptic Package Manager) just type "wacomcpl" (with out the quotes) in a terminal and the gui will pop up.  You may have stylus in "hover mode" and a TPC off problem.  To keep the wacomcpl settings through a reboot see "Section 3:  Calibrating your tablet" here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Eraser only works in programs that can handle it like Gimp and Inkscape.  See near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  In Xournal the stylus button is the eraser.

---

### Post by theCroc on 2009-09-05
I simply did the 10-wacom.fdi replacement you gave in a thread I cant find. Thanx to that I can now reach the different devices in the wacomcpl. however there doesn't seem to be a calibration button in there (Which confuses me because I've used it before on a tx2000 tablet pc with success. 

I did have a custom_wacom.fdi in there from a previous attempt. removing it had no discernible effect. 

I'm using the linux wacom 0.8.2-2 driver right now. Will upgrading do anything to fix this?

---

### Post by Favux on 2009-09-05
Hi theCroc,

Good.  Removing the custom .fdi was probably needed.  The modified 10-wacom.fdi is at post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

I don't know why there isn't calibration.  Maybe due to your tablet model?

I doubt upgrading the linuxwacom would help.  I think the Wacom volito2 is old enough that 0.8.2-2 should have complete support.

Did the pen clicking straighten out?

---

### Post by theCroc on 2009-09-05
No it's still doing it. Is there a way to access the config files directly? I couldn't find anything about hover mode in the wacomcpl

---

### Post by Favux on 2009-09-05
Hi theCroc,

When the wacomcpl gui pops up and you click on stylus do you see tool buttons?  Change side switch mode to side switch + stylus tip.  Also go into Feel and maybe adjust Suppress Points.  Be sure to note you're previous/default settings.

If you are not seeing these things it's possible you have a linuxwacom version conflict.  Both xserver-xorg-input-wacom and wacom-tools need to be the same version otherwise you can run into problems.  What version does Synaptic Package Manager say you have?

You didn't try to install a non-default version of linuxwacom, did you?

The .xinitrc file wacomcpl generates is a hidden file so in View you have to check Show Hidden Files.  The LWP HOWTO shows you the xsetwacom commands for calibrating and configuring:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

### Post by theCroc on 2009-09-21
Hi again. I upgraded to Karmic alpha 6 and the strange clicking behaviour is gone. Actually the pad works out of the box with no fdi editing etc. However now I don't have pressure sensitivity. You wouldn't happen to know where I can adjust this?

---

### Post by Favux on 2009-09-21
Hi theCroc,

Well I'm sure you know how to set up Gimp or whatever for pressure.  There's also the xsetwacom command for the pressure curve which wacomcpl automatically generates.
> PressCurve    i1 i2 i3 i4              sets the pressure bezier curve, where i1+i4=100; i2+i3=100
From:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)
And would look something like this:
```
xsetwacom set stylus PressCurve "0 10 90 100"
```

But since it's alpha there could be any number of bugs in any number of different things causing that.  Making it hard to track down.

Loic2 is just starting to look into Karmic.  Right now Karmic has the 0.8.3-2 version of linuxwacom.  Loic2 provides a link to Timo's 0.8.4-1 linuxwacom packages.  He's trying to get them included into Karmic replacing the 0.8.3-2's as default.  See post #309 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=31](http://ubuntuforums.org/showthread.php?t=967147&page=31)

Maybe the new packages will fix your pressure.  Or at the worst you'd be helping to get 0.8.4-1 into Karmic.

---

### Post by theCroc on 2009-09-23
Turns out pressure was working in Karmic. It was just a matter of activating the general "Wacom Volito 4x5" and none of it's children (Cursor, eraser ec.) in the Gimp.

However for the sake of adventure I will try the newer packages as well.

---

