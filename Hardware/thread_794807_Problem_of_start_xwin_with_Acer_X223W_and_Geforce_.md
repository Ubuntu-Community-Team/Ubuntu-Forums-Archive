---
title: "Problem of start xwin with Acer X223W and Geforce 9600 ET"
date: 2008-05-15
forum: Hardware
---

### Post by carfield on 2008-05-15
I cannot start xwindows for my new company, I've read this Guide http://myy.helia.fi/~karte/acer_al2216w_-_22_inch_monitor_with_linux.html but doesn't help, 

1)  &#8216;sudo dpkg-reconfigure xserver-xorg&#8217; doesn't ask me any question about graphic card and monitor, it only ask what is my keyboard.
2) I've manually add following section to xorg.conf, doesn't help also

```
Section "Monitor"
   Identifier "Acer AL2216W"
   ModelName "Acer AL2216W"
   HorizSync 31.5 - 67.0
   VertRefresh 50.0 - 75.0
   Modeline "1680x1050" 149.00 1680 1760 1944 2280 1050 1050 1052 1089 -hsync +vsync
   Option "DPMS"
EndSection
```


```
   SubSection "Display"
      Depth 24
      Modes "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
   EndSubSection
```

3) I am not using intel chipset, when I try to add 
Driver "nvidia"
or 
Driver "nv"
doesn't help either...

What should I do?

---

### Post by carfield on 2008-05-15
My bad... actually ubuntu able to auto config it, the problem is I use dual monitors. How can I config ubuntu for dual mon?

---

