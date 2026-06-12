---
title: "Set resolution on headless server"
date: 2015-09-29
forum: Hardware
---

### Post by seattle vic on 2015-09-29
I've added a server to my little farm but have run out of monitors, so when I vnc in (using x11vnc), Ubuntu 15.04 doesn't detect a monitor and defaults to a smaller resolution than I'd like.  If I connect the monitor it ramps up to 1920x1080.  I haven't messed with xorg.conf in years it seems but now I can't find it.  Seems like it used to be in /etc/X11/ so I'm guessing that the X conf files have changed.  I could use some help as to where the conf file is for me to set the resolution.

Thanks in advance...

---

### Post by seattle vic on 2015-09-29
OK, so after a "lot" of googling, it came down to two things.

1. Insert a dummy video driver: sudo apt-get install xserver-xorg-video-dummy
2. Since there's no default xorg.conf file that I could find anywhere, AND there are several locations where you can supposedly put it (/etc/X11, /usr/share/X11, ~)  I created one and placed it in /etc/X11:

```
Section "Device"    Identifier  "Configured Video Device"
    Driver      "dummy"
    VideoRam 256000
EndSection


Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 5.0 - 1000.0
    VertRefresh 5.0 - 200.0
    ModeLine "1920x1080" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +Hsync +Vsync
#    Modeline "1280x800" 24.15 1280 1312 1400 1432 800 819 822 841
EndSection


Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1920x1080"
    EndSubSection
EndSection
```

I just wanted one resolution and this did the trick.

---

### Post by weatherman2 on 2015-09-29
Which version of Ubuntu did you use this on?  And which flavor (Ubuntu?  Kubuntu?)  It seems that the solution to this is different with each new version of Ubuntu.  So the actual version/flavor your solution worked on might help people who discover this thread in the future.

---

### Post by seattle vic on 2015-09-29
> **weatherman2 said:**
> Which version of Ubuntu did you use this on?  And which flavor (Ubuntu?  Kubuntu?)  It seems that the solution to this is different with each new version of Ubuntu.  So the actual version/flavor your solution worked on might help people who discover this thread in the future.

Yeah, I struggled with it for about 5 hours so figured I post it for others.  I'm running Ubuntu 15.04.  Once I knew that X does pick up the xorg.org file in /etc/X11, the real challenge was to find the settings that work.  I haven't messed with them in probably 3 or 4 years so I had to look at posts, articles, etc where different people had also struggled.  I probably tried 5 or 6 versions before I hit on the one that worked.

---

### Post by weatherman2 on 2015-09-30
Thanks.  It will probably help me, too.

---

### Post by steeldriver on 2015-09-30
It seems to me you are making life more complicated than it needs to be, by running a "real" X session on a headless box and then using x11vnc

If you invoked a standalone vncserver instead, you could simply set whatever display geometry you like on the command line

---

### Post by seattle vic on 2015-09-30
Good point.  I hadn't really considered that.  I want the flexibility to hook up a monitor if things really go south but I guess I could always bring up X in that case.  Thanks for the tip.

---

