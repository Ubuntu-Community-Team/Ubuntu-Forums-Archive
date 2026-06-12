---
title: "How to fix Intel Graphics Hibernation Issue"
date: 2010-04-05
forum: Hardware
---

### Post by jbayone on 2010-04-05
[FONT="Verdana"]
So after installing Kubuntu netbook remix on an older Pavillion DV1000 laptop, everything was going smooth for a while, that is until the battery started to drain and it went into hibernation mode.  I plugged it back in after a couple of hours, pressed the power button and the wake button on the laptop and got no response.  The BIOS, GRUB, and everything prior to the initial splash screen worked as they should.  The issue arose immediately afterward when I was greeted by a completely black screen. 

I tried Control - Alt - F1, but the screen didn't even flicker or go to CLI.  I was like, "wtf man?" After that, I tried booting into Recovery Mode hoping I could get at least something.  Not even editing different commands in GRUB could do anything to thwart this beast.  I got the idea to hook up an external monitor, and after rebooting, it showed up, resolution on that one was 1284x1024 but the screen was really shaky and way off center, the highest resolution bearable was 1024x768.  After I was logged in, I checked Display settings and saw the monitor "LVDS1I" (the laptop monitor)was listed, but everything was grayed out as if it wasn't accessible. I unplugged the external one hoping it was the switch over, but to no avail.  I tried to 
```
dpkg-reconfigure xorg
```
 I checked the forums, Launchpad, Google...everything I could think of, and no suggestions could resolve it.  Most solutions pointed to Nvidia and ATI cards but this old thing has an Intel graphics chipset.  

There was one useful thread - 
```
Quote:
Due to a known bug, on some laptops with Intel video adapters, if the display goes into sleep mode with the laptop lid closed, it will not be reactivated when the laptop lid is opened. The display will stay blank unless you reboot or use the following workaround. To workaround this problem, create a file with the following contents:
Code:


   
          !/bin/bash
          xrandr --output LVDS1 --off
          xrandr --output LVDS1 --auto


and save it as ~/screenfix.sh. Make it executable, and assign it to a keyboard shortcut (the method for doing this depends on your desktop environment). Executing this script via the keyboard shortcut should bring the display back to life. Note that the output parameter may vary; you can see the appropriate value for your system by running xrandr at a console and examining the output. A fix for this issue has been committed to the upstream kernel and may be made available in a future Fedora 12 kernel update. 
```
While that may have worked, before I tested it out, I decided, "well, if this all began by the battery dying, let me take it out, boot it and see what happens.  Lo and behold, it booted right up to the kde splash-screen.  I added that bash script with a keyboard shortcut just in case, since that was a fix for a bug in intel chipsets at one point.

While it may not be appropriate to your notebook sleep/hibernation issue, maybe someone else still has an intel chipset running Ubuntu or Fedora.  Try booting without the battery, says Oolon Colluphid&#8206;.
[/FONT]

---

