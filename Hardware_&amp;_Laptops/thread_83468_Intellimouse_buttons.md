---
title: "Intellimouse buttons"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by James Reed on 2005-10-28
I have gotten the forward/back buttons and scroll wheel to work from the info in the WIKI. Now how do I get them to operate properly. Currently, the scroll wheel acts as the forward/back buttons and the forward/back buttons act as the scroll wheel. This needs to be reversed.

Thanks

---

### Post by Appolusionist on 2005-10-28
[quote=James Reed]I have gotten the forward/back buttons and scroll wheel to work from the info in the WIKI. Now how do I get them to operate properly. Currently, the scroll wheel acts as the forward/back buttons and the forward/back buttons act as the scroll wheel. This needs to be reversed.

Thanks[/quote]

You did not provide any of your config files, but I had the same problem. I followed this [wiki]("https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons") and had to edit the "ZAxisMapping" from "6 7" to "4 5". Below is the Mouse Input Device section from my /etc/X11/xorg.conf

> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Resolution"            "100"
EndSection

---

### Post by James Reed on 2005-10-29
That was it. Change the buttions "6 7" to "4 5". Now the Intellimouse works normally.

Thanks

---

