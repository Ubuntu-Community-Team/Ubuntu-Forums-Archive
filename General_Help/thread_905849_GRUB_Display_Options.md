---
title: "GRUB Display Options"
date: 2008-08-30
forum: General Help
---

### Post by Milliways on 2008-08-30
Can I set the display size from the GRUB boot menu?

I have an Ubuntu 7.10 computer, which I haven't used for a while.
It needed a new power supply, which I have installed, but boots up to 1280x1024 pixels, which is not supported by the monitor in my workshop (1024x768).

I can access by VNC & putty.

---

### Post by retrovertigo on 2008-08-30
You can try manually editing /etc/X11/xorg.conf.  Make sure to back it up first!  You'll want to make changes to the "Screen" section specifically.  Here's an example, you may need to make a couple changes but I tried to make it mesh with the xorg.conf file on my machine:

```
# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Default Screen"
    Device      "Configured Video Device"
    Monitor     "Configured Monitor"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1024x768" "800x600"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1024x768" "800x600"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600"
    EndSubsection
EndSection
```

Restart the computer, and it should start X with a resolution of 1024x768.  You can then run **sudo dpkg-reconfigure -phigh xserver-xorg** to give Ubuntu control of your display settings again.  Hopefully it won't set the default back to 1280x1024.

---

