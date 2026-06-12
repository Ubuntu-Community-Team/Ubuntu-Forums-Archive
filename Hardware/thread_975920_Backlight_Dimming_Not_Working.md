---
title: "Backlight Dimming Not Working"
date: 2008-11-08
forum: Hardware
---

### Post by Shwefty on 2008-11-08
I've checked around and haven't found a fix for this yet.

I run a Toshiba Satellite A105-S4004 dual booting Intrepid and XP (Media Center).  Back in Hardy, my screen dimming functionality w/ Alt-F6/Alt-F7 wasn't working, and here in Intrepid, still not working.  Also not working is the Power Management "Reduce Backlight Brightness" option or the brightness slider as an item on the panel.

Anybody have any ideas?  Thanks in advance!

---

### Post by mbeach on 2008-11-08
not alone - perhaps this pertains to you:

see post 3 at:
[http://ubuntuforums.org/showthread.php?t=975464](http://ubuntuforums.org/showthread.php?t=975464)
and the associated bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/261721](https://bugs.edge.launchpad.net/ubuntu/+bug/261721)

---

### Post by Shwefty on 2008-11-08
Thanks for the very quick reply!

As for the links, I've never gotten any artifacts or aliasing or anything of the sort. Essentially, I get nothing on the shortcut.  Also, I can't seem to dim my display in any fashion I've found (haven't touched Terminal yet).

---

### Post by wgrant on 2008-11-08
Try gnome-power-manager from [my PPA](https://launchpad.net/~wgrant/+archive).

---

### Post by Shwefty on 2008-11-08
Tried it.  I honestly don't know what I installed, but it said it was replacing the default Power Management (which gives me the willies, but, it's done).  However, I still don't seem to have dimming functionality.  I tried the Brightness Applet, Power Management, and the alt-f6/alt-f7 again.

I should mention that my laptop has integrated graphics.

Thanks for the heads up!  But, still not working as of yet.

---

### Post by xx404 on 2008-11-08
Does your Toshiba have a Phoenix BIOS? As far as I know you're pretty much out of luck. All the Toshiba related Linux utilities are designed to work with the Toshiba BIOS so won't work with one that has a Phoenix BIOS. Some users seem to have had some luck by upgrading their BIOS so if you don't have the latest version you can try that - but beware; the BIOS upgrade for some models restricts the OS to Vista!

---

### Post by wgrant on 2008-11-08
> **Shwefty said:**
> Tried it.  I honestly don't know what I installed, but it said it was replacing the default Power Management (which gives me the willies, but, it's done).  However, I still don't seem to have dimming functionality.  I tried the Brightness Applet, Power Management, and the alt-f6/alt-f7 again.

I should mention that my laptop has integrated graphics.

Thanks for the heads up!  But, still not working as of yet.

You'll need to log out and in again for the changes to take effect.

---

### Post by Shwefty on 2008-11-09
First of all, for the BIOS info, the laptop specs has this to say about the BIOS...and I have no idea what it means, but I don't think it's Phoenix:

BIOS
     - TSETUP, APM v 1.2, ACPI v1.0b, PNP v1.0, VESA, DPMS, DDC, SM BIOS v2.3, PCI BIOS v2.1 support.

I tried some command line stuff to get it to tell me, but it didn't work.

I did a full reboot, but it's still not working.  Like before, I still have the brightness slider (even the brightness pop-up when unplugging my laptop), but there's no dimming.

Thanks again!

---

### Post by Shwefty on 2008-11-13
5 days = bump time

---

