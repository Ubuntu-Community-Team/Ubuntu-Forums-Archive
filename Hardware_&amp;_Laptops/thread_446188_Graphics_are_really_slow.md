---
title: "Graphics are really slow"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by acb5042 on 2007-05-16
Ubuntu runs really slow on my machine. It's not neccesarily how fast programs start up or run, but how slowly they render on my screen. I've searched the forums about this and it seems to be my Integrated Graphics which don't have drivers. This problem happens a lot, apparently.

After running lspci, I get:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

My /cat/X11/xorg.conf file states:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection
```

I'm sure that's not what it's supposed to say. From there, I haven't found too many instructions. I've seen that I need to download a i806 driver. Is this true? Where do I find this? How do I set it up?

The slow rendering is unbearable!

---

### Post by Kobalt on 2007-05-16
Open up Synaptic package manager, search for *xserver-xorg-video-intel*. Select it and install it, then restart. That should do it.

---

### Post by acb5042 on 2007-05-16
Thank you so much! You also have to change the xorg.conf file to say that you are using the intel driver. Everything works so fast. I added the desktop effects and they are seriously kick ***. They make my system run a bit slower so I may take them off, but all I have to say is wow and thank you.

---

