---
title: "upgrade to 9.10 Karmic Koala - full screen windows including desktop are black"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by bolind on 2009-11-01
Hello

I've upgraded to 9.10 from whatever the latest stable was before... 9.04 I guess. Now, every window, unless not-maximized, has black content. This includes the desktop, I guess it's technically also a window, albeit borderless.

The funny thing is, that stuff is there. If I click the right places on my very black desktop, I get my files.

Hardware: IBM Thinkpad T40p. lspci says: 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

I had some compiz enabled previously... dunno if that makes a difference.

Help!

Edit:

Relevant section of xorg.conf:

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1400x1050"
        EndSubSection
EndSection

---

### Post by bolind on 2009-11-01
Well, I "solved" the issue by disabling all screen effects (System -> Preferences -> Appearance -> Visual Effects -> None), but still a bug I guess.

---

### Post by Turtle.net on 2009-11-01
We are discussing the same problem [here]("http://ubuntuforums.org/showthread.php?p=8218583#post8218583").

---

