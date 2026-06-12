---
title: "No Backlight at Login Screen"
date: 2009-02-08
forum: Hardware
---

### Post by oldnoob on 2009-02-08
Sorry for the long post...  This is an annoying problem I've been researching this for three days and trying different things with no success.

I've been running 8.04 on a Dell C640 for about 3 months.  Throughout this period, I would have occasional issues with the LCD backlight not working during bootup.  In most cases, if I unplugged the power for a second, the display would be fine.

About 7-10 days ago, when I bootup with the power plugged in, the backlight is off unless I do the quick unplug/plugin trick.  During the bootup process, I can see everything, and my keyboard brightness keys work fine - I can dim and brighten.  After the Ubuntu load status bar completes and disappears, but before the login screen appears, the backlight goes off.  Then the login screen comes up but I can barely see it, but it's useless other than to shutdown via Alt-T > D > Alt-D.

Now, if I unplug the laptop during the bootup before the Ubuntu load status bar completes, the backlight will turn on fine, but it is dimmed per the BIOS settings.  I can login and work, but the brightness controls are non-functional.  The applet moves, but nothing happens, and Fn DnArrow/UpArrow do nothing.  Even if I reconnect the power, the display stays in the dimmed mode.  If I go into the BIOS and set the "battery" display brightness higher than halfway, the display may not turn on at all during bootup.  I've had to reflash the BIOS from a CD to reset the defaults and allow me to boot up again with a working display.

If I connect an external monitor before booting up, all is fine whether on AC power or battery.

I don't know if this is ACPI related, if a recent update did something, or if it could be hardware (LCD inverter).  I've tried adding a line /etc/init.d/gdm to set brightness to 100% at the login screen but it had no effect.  I've tried disabling power management in the BIOS, and setting acpi=off during bootup. 

I have a Dell C640, running Hardy 8.04, 2.6.24-23-generic, GNOME 2.22.3.  Video driver is Radeon Mobility M7 LW (ATI Radeon 7500). My BIOS info is
841-BIOS Information
858:	Vendor: Dell Computer Corporation
893-	Version: A10
1782-	Manufacturer: Dell Computer Corporation
1823:	Product Name: Latitude C640                   
1871-	Version: Not Specified
--
2056-	Manufacturer: Dell Computer Corporation
2097:	Product Name:       
2119-	Version:    

THANKS!

---

