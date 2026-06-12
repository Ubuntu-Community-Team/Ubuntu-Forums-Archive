---
title: "Monitor no longer detected"
date: 2020-09-08
forum: Hardware
---

### Post by Colin@oxford on 2020-09-08
On booting my desktop computer, it only intermittently detects the monitor and when it does not, sets me up in VESA mode with very low resolution.  It used to work fine.  I thought it was a slightly loose connection (which when I tightened it worked fine, but now it has gone wrong again and there is nothing obviously loose).  In VESA mode, running xrandr gives:
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)

```
inxi -Fxz gives for the Monitor section:
```

Graphics:  Card: Intel Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics (ILK)
           version: 2.1 Mesa 20.0.8 Direct Render: Yes

```

The cable is HDMI but has an adapter at the monitor end.

Any suggestions as to whether this is a problem with the card, cable or monitor?

---

### Post by Autodave on 2020-09-08
Could be all 3 of them.  I would start with the cable and the adapter.  Remove and install them a couple of times and make sure that you also do the adapter to cable connection.  You may just have a dirty connection.  If no luck, try another HDMI cable.

---

### Post by Colin@oxford on 2020-09-08
Thanks, I've tried that and all is OK at the moment.  We'll see what happens on the next boot....

---

### Post by Autodave on 2020-09-08
Cables break internally and connectors get worn, loose, or corroded.  The adapter can get loose.  Always keep at least one spare of each around.

If that fixed the problem, please remember to marked this as "Solved".  You can find that at the top of this thread.

---

