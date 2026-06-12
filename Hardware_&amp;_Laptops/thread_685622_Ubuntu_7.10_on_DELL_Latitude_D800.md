---
title: "Ubuntu 7.10 on DELL Latitude D800"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by tommar on 2008-02-02
I would consider myself an advanced Linux beginner. I have got a DELL Latitude D800 laptop and installed Ubuntu 7.10 on it (after having installed Windows XP for some educational games I needed for my kids).

Almost everything seems to work out of the box. In this thread I want to document (also for myself) what needed to be adjusted.

**Making nvidia work with suspend function**

Ubuntu has asked me to confirm the use of non-proprietary drivers for the NVIDA graphics card and the miniPCI wireless interface.I did. NVIDA (the nvida-glx package) needs some minor adjustments. First of all, screen resolution was not detected automatically. However, I just needed to change the screen resolution to 1920 x 1200 in System -> Administration -> Screen and Graphics. You need to check "widescreen", this does not happen automatically.

The first real problem I faced was that the suspend function did not work. After suspending the system would not start up again. One reason, as I found out, MIGHT be USB hardware. For testing purposes it's a good idea to remove all USB devices before suspending the system. The main reason are two changes necessary in two configuration files:

1) in /etc/X11/xorg.conf zou need to add in the "Device" section

     Option     "NvAGP"     "1"

2) in /etc/default/acpi-support POST_VIDEO must be set to false.

Both options have to be changed and the suspend function works perfectly.

**Keyboard**

All keyboard functions seem to work out of the box. However, I changed the keyboard setting from standard to a special Dell Latitude keyboard. Did not realize any differences, though.

Cheers,

tommar

---

### Post by tommar on 2008-02-02
I had some problems to enable Flash in Firefox and still did not work out how it works. The non-free Marcomedia player can be installed but is not recognized as installed by Firefox.

I then switched to the Gnash SWF player (which is recognized as Flash 6.0) but this one does not seem to work perfectly. Any ideas appreciated...

---

### Post by nordge1 on 2008-04-26
Tommar
I have a Dell Latitude D800 as well with Ubuntu 7.10. I am an extreme newbie to Ubuntu and Linux in general. I have yet to overcome the flash recognition issue. Have you made any headway?

---

