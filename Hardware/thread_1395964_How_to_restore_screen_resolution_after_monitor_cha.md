---
title: "How to restore screen resolution after monitor change?"
date: 2010-02-01
forum: Hardware
---

### Post by pinkunicorn on 2010-02-01
For some time, I've been using 1600x1200 resolution with a Compaq 2025 monitor with no problems. 

However, that monitor just broke down and I got myself an HP L2245xg which is supposed to handle 1680x1050, but when I connect it I only get 1280x1024.

```
$ xrandr
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

```

I don't have any /etc/X11/xorg.conf.

I've tried dpkg-reconfigure xserver-xorg which appears to do nothing at all.

How do I get back to the top resolution again?

---

### Post by ghostborg on 2010-02-01
Did not see an xg out there but it might help others if you could indicate what your graphics card is.

L2245w/L2245wg Model
screen                    22 inches wide screen

     Maximum Graphic Resolution              1680 x 1050 (75 Hz) analog input
                                             1680 x 1050 (75 Hz) digital input
     Optimum Graphic Resolution              1680 x 1050 (60Hz) analog input
                                             1680 x 1050 (60Hz) digital

---

### Post by pinkunicorn on 2010-02-01
I don't know what xg is, but my graphics card presents itself as "VGA compatible controller: Matrox Graphics, Inc. MGA Parhelia AGP (rev 03)".

---

