---
title: "Help with xorg.conf"
date: 2010-03-19
forum: Hardware
---

### Post by weaver4 on 2010-03-19
I am using Ubuntu 9.10 on a Jetway motherboard which has a atom processor and a Intel 945GSE+ICH7M chipset.

I am getting bad tearing in the vga output.  My monitor has a bunch of horizontal lines in it.

So I decided to try the VESA driver and the screen looks OK, but no matter what I do the resolution is 1024x768 and I want 1280x1024.  Here is the xorg.conf file I created.  Can someone tell me what I am doing wrong?  The modeline was created by using "cvt 1280 1024 60"

```

Section "Device"

        Identifier      "Configured Device"

        Driver  "vesa"

EndSection



Section "Monitor"

        Identifier      "Configured Monitor"

        HorizSync 31-65  

        VertRefresh 50-75

	Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

EndSection



Section "Screen"

        Identifier      "Default Screen"

        Monitor         "Configured Monitor"

        Device          "Configured Device"

        SubSection "Display"

                Depth           24

                Modes           "1280x1024"

        EndSubSection

EndSection


```

---

