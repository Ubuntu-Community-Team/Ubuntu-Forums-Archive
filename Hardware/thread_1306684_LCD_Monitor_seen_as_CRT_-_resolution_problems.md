---
title: "LCD Monitor seen as CRT - resolution problems"
date: 2009-10-30
forum: Hardware
---

### Post by flatwombat on 2009-10-30
Just installed Ubuntu 9.10, 32 bit, and my standard 17" LCD monitor is not recognized.  Instead, I'm stuck with system defaults and a max resolution of 800x600 (640x480 after installing the nvidia drivers). Since the other 7 distros I'm booting are happily finding the monitor and I'm used to 1024x768, I'm not enjoying the experience.

In the hopes of tweaking /etc/X11/xorg.conf, I've grabbed info from my Mint partition as well as my Fedora partition to TRY and explain to KK that I really do want something more.  Here's what I've got so far, which hasn't made the slightest difference:

> Section "Screen"
        Identifier      "Configured Screen Device"
        DefaultDepth    24
SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
    VendorName     "Cornea"
    ModelName      "LCD"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Also, this is from my /var/log/Xorg.0.log

> (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 30 15:55:11 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Configured Screen Device" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Configured Screen Device".
        Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Configured Screen Device".
        Using a default monitor configuration.

Aha!  It caught my attempt to say that it was a Configured Monitor when it wasn't.  I suppose I could change that to default monitor, but I don't see how that's going to fix it.  So, I'd appreciate it if someone could point out what I've missed including.

---

### Post by flatwombat on 2009-10-30
BTW, changed the configured monitor to "monitor0" and rebooted.  No change. *sigh*

Edit: Also tried the xrandr options; no difference.  Every boot, I have the Configure Display Settings icon popping up since apparently Ubuntu can't find a monitor or understand what it sees.

Interesting that I seem to be the only one with this problem and that there seems to be nothing in the wiki about correcting such events.  I've had a long history with Ubuntu and I'd hate to see it end here.

---

### Post by flatwombat on 2009-10-30
Well, how about that!  After removing the Nvidia drivers and not getting full resolution in vesa or nv, I reinstalled the Nvidia drivers and THIS time, I'm happily at 1024x768 with no problems!

So, did I use the wrong drivers the first time?  Did something finally convince Ubuntu to use the xorg.conf that I had modified (and which is still there) or was it something else?  Who knows?  But this problem is essentially 'solved' for me. ;)

---

