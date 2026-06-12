---
title: "Synaptics clickpad occasionally sends only right-click"
date: 2014-05-19
forum: Hardware
---

### Post by tobyS23 on 2014-05-19
Hi,

in my X240 I use the synaptics clickpad (no physical buttons) for clicking only and disabled the pointing/scrolling functionality through the driver as follows:

```

$ cat /etc/X11/xorg.conf.d/99-x240-clickpad.conf 
Section "InputClass"
    Identifier "tp only with clickpad buttons"
    MatchDriver "synaptics"
    Option "SoftButtonAreas" "60% 0 0 0 45% 59% 0 0" #Emulate right and midle buttons
    Option "AreaBottomEdge" "1" #disable moving but not buttons
EndSection

```

That works pretty well and did not cause any trouble until ~1 week ago. Since then, the clickpad occasionally seems to send only right-click events (i.e. clicks in the configured area for right-clicking). AFAICS only rebooting the system fixes the issue.

I wonder if anyone else is experiencing the same?

Regards,
Toby

---

