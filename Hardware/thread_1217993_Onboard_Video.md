---
title: "Onboard Video"
date: 2009-07-20
forum: Hardware
---

### Post by stevie1989 on 2009-07-20
My monitor on my laptop is going out on me, now l have a old crt monitor l can plug it into, and works in Vista, but won't be able too use kubuntu anymore if l can't see the screen. Any ideas would help alot. 
DV2620ca
[http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12139188-78299199-78299212-78299212-78299212-80632394.html](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12139188-78299199-78299212-78299212-78299212-80632394.html)

---

### Post by komputes on 2009-07-20
Boot into recovery mode using these instructions: [https://wiki.ubuntu.com/RecoveryMode?action=show&redirect=BootingIntoRecoveryMode](https://wiki.ubuntu.com/RecoveryMode?action=show&redirect=BootingIntoRecoveryMode)

and then select the xfix script to reconfigure the video. You can then resume normal boot. If your video does not work after that, press ctrl-alt-f1 and if you can see the command line, you at least have that way of modifying configuration files, so it is possible to try the vesa "lowest common denominator" driver.

---

### Post by stevie1989 on 2009-07-20
Did the xfix, no luck. Now about the other option, how do l set the lowest denominator?
bump

---

### Post by komputes on 2009-07-20
To use VESA mode you would need to edit the devixce section of xorg.conf file and set the driver manually.

1) Open xorg.conf for editing
```
sudo nano /etc/X11/xorg.conf
```

2) Change the device section to specify that you want the vesa driver loaded. The before will look like:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection
```

And the after:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection
```

Then simply restart and you should be able to get a low resolution graphical desktop.

---

### Post by stevie1989 on 2009-07-22
This is what l get:
> # again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "True"
EndSection


---

### Post by stevie1989 on 2009-07-24
So should l change the following:
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection




Too


 Section "Device"
         Identifier      "Configured Video Device"
         Driver "vesa"
         Option  "NoLogo"        "True"
 EndSection
 
 ???

---

