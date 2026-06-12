---
title: "Edgy Eft: &quot;Failed to load module 'kbd' (module does not exist)&quot;"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Roobert on 2006-10-27
I've just 'upgraded' from Dapper to Edgy. My xserver is now broken. I have a ATI X300 video card. I've tried dpkg-reconfiguring xserver-xorg about 20 times, using ATI, vesa, with and without framebuffering, etc,etc. 

Output from xserver's anaylsis says:
```
(EE) Failed to load module "kbd" (module does not exist, 0)

(EE) Failed to load module "mouse" (module does not exist, 0)
RADEON: No matching device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected
```
I want to do a complete reinstall from the ISO cd, but when I reboot, a get a blank screen - how can I reinstall from the menu when I can't see *anything* on the display?

Or, alternatively, can anyone think of what is causing this error?

~ Roobert.

---

### Post by Krash1201 on 2006-10-27
i am having a similar problem on a t42p with an ati fire gl t2 graphics card, though i haven't tried to reconfigure xorg.  When i boot up i get an xorg crash that indicates the ati drivers are the problem.  any ideas on how to fix xorg and the ati drivers?

---

### Post by Roobert on 2006-10-31
I have no idea. This is getting to be a bit ridicluous, actually. I'm going on 5 days now with no display and a broken xserver. None of the posted ATI tricks have worked:

1. Changing 'Device' in /etc/X11/xorg.conf to "vesa"
2. Changing 'Device' in /etc/X11/xorg.conf to "ati"
3. Enabling linux-restricted-modules and changing 'Device' in    /etc/X11/xorg.conf to "fglrx"
4. Changing 'Device' in /etc/X11/xorg.conf to "vga"

I'm using the X300 driver. The last line of my /var/log/Xorg.0.log says ```
Fatal sever error:
failed to initialize core devices
```

I haven't encountered any other ATI users who have had that problem, which is probably why none of the fixes work on my mahcine.

What else can I try?

---

### Post by Gaara on 2006-11-06
I had the same problem.

Running sudo apt-get install xserver-xorg-video-ati followed by
sudo dpkg-reconfigure -phigh xserver-xorg fixed it.

Hope it helps.

---

