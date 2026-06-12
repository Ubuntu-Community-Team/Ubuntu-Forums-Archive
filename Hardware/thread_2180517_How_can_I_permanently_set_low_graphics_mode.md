---
title: "How can I permanently set low graphics mode?"
date: 2013-10-13
forum: Hardware
---

### Post by andrew732 on 2013-10-13
I've given up trying to solve my graphics hardware problems in 10.04, but I don't care any more because everything works fine once I run in low graphics mode.  The only problem is that every time I reboot I have to wait several minutes for Ubuntu to figure out that my graphics aren't going to work before it gives me the option to run in low graphics mode, which is extremely annoying.  How can I make this setting permanent?  I don't seem to have any GUI tools for graphics management in System->Preferences or System->Administration, except for a "Monitors" GUI that has no options I can set.  Thanks for any help you can give.

---

### Post by Yellow Pasque on 2013-10-13
Try making basic /etc/X11/xorg.conf:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by andrew732 on 2013-10-18
Thanks for your reply, but that doesn't appear to change anything.  What lines would I have to add to xorg.conf to permanently enable low graphics mode?

Anyone know how to do this?

---

### Post by andrew732 on 2013-10-20
Anyone know how to do this?

---

### Post by Yellow Pasque on 2013-10-20
Post your /var/log/Xorg.0.log


> What lines would I have to add to xorg.conf to permanently enable low graphics mode?
Driver "vesa" was supposed to do it.

Maybe you should install a supported version where your graphics work..

---

