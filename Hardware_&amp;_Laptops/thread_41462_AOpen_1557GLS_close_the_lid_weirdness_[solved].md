---
title: "AOpen 1557GLS close the lid weirdness [solved]"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by matthew on 2005-06-13
I have a rebranded AOpen 1557GLS (bought from CyberPower, Inc...but it is exactly the same thing). It has the ATI Mobility Radeon 9700 video card using the fglrx 8.08.25 driver. Everything is working beautifully which is why I haven't upgraded the driver yet. However, since I finally got the ATI driver working I have noticed that every time I shut the lid of my laptop instead of merely blanking the screen and then coming back on when I open it something strange happens. The screen blanks as expected when the lid closes, but when I open it back up the color of the screen changes horribly, changing blues to neon pink and randomly changing the look of the desktop to unusability. The problem does not go away if I switch using <ctrl><alt>F* and back to  F7. However, if I log out and log back in all is restored.

This isn't a huge issue, but I am at a loss to explain it or know what to do to prevent it, so I find I have to keep the laptop's lid open at all times unless I want to logout/back in. Does anyone know what might be causing this and what I might be able to do to prevent/fix it?

---

### Post by Davor281 on 2005-06-13
Hi!

I don't know if this is the same problem, but I do remember that ATI drivers had some problems with such situations.

The only post that is somehow close to your problem is here:

[https://support.ati.com/ics/support/default.asp?deptID=894](https://support.ati.com/ics/support/default.asp?deptID=894)

ENjoY!

Davor.

---

### Post by matthew on 2005-06-13
Thanks. Interesting reading. I wonder if this is something that is being worked on? I didn't have the problem before I installed the ATI driver...of course, I didn't have 3D capability then either and it's a trade I'm willing to make.

---

### Post by u-blunt-2 on 2005-11-08
Same problem with my laptop and ATI RADEON mobility 9700...
Is there some way to restart X-server without disrupting any operating applications ?

---

### Post by matthew on 2005-11-08
When I was using Hoary (Ubuntu 5.04) I never figured out how to restart the x server without something being disrupted. I probably could now, but once I switched to Breezy (Ubuntu 5.10) on this laptop the problem went away.

I can now close the lid and the screen goes blank. When I open the lid I am asked for my password and all works perfectly.

EDIT: FYI, after installing Breezy I installed the fglrx driver from the repositories, version 8.16.20, and have full 3D acceleration with no graphics problems whatsoever. I am still unable to hibernate this machine. No hardware changes have been made.

If you don't want to upgrade to Breezy (I assume you are still using Hoary only because I haven't had a single problem with this since the upgrade) you could try this...I'm sorry I can't test it for you with the same malfunction, though.

Close lid. Open to discover weirdness.
Press Ctrl+Alt+F1
Log in at the console that appears
Type```
sudo /etc/init.d/gdm stop
```followed by ```
sudo /etc/init.d/gdm
``` and see if stopping and restarting gdm kills your other running programs or not. I think anything that needs gdm (Gnome Display Manager) or was using xserver in any way will be shut down, but other processes won't.

---

### Post by u-blunt-2 on 2005-11-09
Sweet ! 
I will bee switching to breezy as soon as possible :p

---

