---
title: "xorg.conf messed up, no backups..."
date: 2008-11-10
forum: General Help
---

### Post by Calmatory on 2008-11-10
Is there a way to restore xorg.conf to it's original state after instalation?

Yes, I've done sudo dpkg-reconfigure -phigh xserver-xorg with no success.

Yes, the machine works, but the touchpad is driving me crazy. Don't tell me to install gsynaptics eihter, I just want the original xorg.conf back. Is there a way to have it back without reinstalling?

---

### Post by justleen on 2008-11-10
uhm, the way get it back is with what you tried..
leave out the-phigh to do a full setup

---

### Post by Calmatory on 2008-11-10
If it should produce the following:
```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
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

Then guess I am out of luck...

---

