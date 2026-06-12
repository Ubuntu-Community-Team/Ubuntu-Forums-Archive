---
title: "Help changing to vesa drivers as default on Lucid Lynx"
date: 2010-07-02
forum: Hardware
---

### Post by fernandoc1 on 2010-07-02
I have the worst Video Card on the world:
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
Everything from SiS is a dirty buggy junk.

When I'm using Ubuntu, the screen gets some lines blinking.
I wish to get the vesa Driver as default.
In Lucid, there is no xorg.conf file in /etc.
Do someone knows a solution to this?

---

### Post by ajgreeny on 2010-07-02
Do you have an xorg.conf.failsafe in /etc/X11?  If so use that as a template but change the "fbdev" to "vesa"

My failsafe version says "fbdev" but I suppose yours may be different.  Whatever it says now change to "vesa" and it should work, though vesa is not good for high resolutions.

Alternatively simply run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` in terminal and an xorg.conf should be produced, I think.

---

### Post by fernandoc1 on 2010-07-02
Do you think that 1440x900 will be supported by vesa?

---

### Post by davidmohammed on 2010-07-02
no - vesa is very basic.  You'll get no 3D effects and probably no more than 800x600.

---

### Post by fernandoc1 on 2010-07-03
The monitor on that computer have a resolution of 1440x900.
Then, as I can see, people with Silicon Integrated Systems should throw their computer away and buy a new one if they need resolutions higher than 800x600.
The driver is too buggy. The screen shows some lines blinking.
Is there any solution to this issue?

---

