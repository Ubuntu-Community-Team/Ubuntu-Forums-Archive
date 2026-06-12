---
title: "KDE unreadable menus"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by bingobingo on 2009-11-12
I just upgraded ubuntu 9.10 and tried to install KDE desktop but none of the menus are readable and right clicking the desktop in K to 'leave' does nothing. I have to 'hardboot' it to shutdown. Is there any effect on not using the default file system ext4?



NEC PowerMate Eco earth-friendly computer

---

### Post by bingobingo on 2009-12-13
My issue was related to the Radeon Driver change that happen in the upgrade to 9.10, but for some reason I still can not shutdown or log off while in KDE. 

Update /etc/X11/xorg.conf

... to look as follows:

Code:
Section "Device"
       Identifier "m6-radeon"
       Driver "radeon"

       # Enabling EXA fixes the notifications
       Option "RenderAccel" "false"
       Option "AccelMethod" "EXA"

       # Xorg will gobble CPU unless you add...
       Option "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       Identifier "laptop-panel"
       Device "m6-radeon"
       DefaultColorDepth 24
       SubSection "Display"
           Depth   1
           Modes "1024x768"
           #Virtual 1024 768
       EndSubSection
EndSection

Section "Extensions"
        # I don't use the compositing settings, so off!
        Option "Composite" "Disable"
EndSection

THEN DO A REBOOT

---

