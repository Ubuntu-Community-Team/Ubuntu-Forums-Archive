---
title: "Switching to external monitor stopped working"
date: 2012-02-08
forum: Hardware
---

### Post by lads on 2012-02-08
Hello everyone,

At work I have a laptop (ThinkPad T420) on a docking station to which an external monitor is connected. I perfer to work solely with the external monitor, it's 22 inch and with 4 workspaces in Unity it is perfectly enough.

When the laptob boots it sends the signal to both the internal and external monitors, then I use the Fn+F7 key combination to go through the several configurations until I have the signal solely in the external monitor. Or at least this is what I used to do, because last week it stopped working. Now when I try the Fn+F7 combination Unity freezes, the mouse still goes around, but all bars are gone, including the window decorations. The only thing I can do is jump to a terminal session and kill the gnome-session process.

Why has this stopped working? Is there anything I can do to get it back to work?

Thank you for the help.

---

### Post by lads on 2012-02-13
bump

---

### Post by cortman on 2012-02-13
Do you want the laptop monitor to be OFF, or just set the external as primary?

If you just want to set the external monitor as primary, a more elegant and foolproof way to do it would be a simple bash script, that you could set to run at startup (and/or run from the terminal any time). Someone else here may be able to post something for you right away, but if not I have one I wrote for my home computer, which I can post this evening. Mine checked to see if the HDMI port was active (or VGA, Mini Display, whatever you use) and if so, to set the external as primary. If not, leave primary on the laptop.

---

### Post by lads on 2012-02-13
> **cortman said:**
> Do you want the laptop monitor to be OFF, or just set the external as primary?

Hi Cortman, I just want the laptop OFF and the external monitor ON, up to 2 weeks ago I'd be able to do this just by pressing Fn+F7.

Thank you for answering.

---

### Post by cortman on 2012-02-13
Hi lads,

I'm not sure of a solution for your Fn+F7 problem, but a simple script (that you could even map to a hotkey combo) would do the job for you.

```
#!/bin/bash

var=$(xrandr | grep 'VGA1 connected')
if [ -n $var ] ;
xrandr --primary VGA1 ;
xrandr --output LVDS1 --off ;
else
xrandr --primary LVDS1;
fi
```

I have not been able to conclusively test this script, but it should work. Make it executable and run it with the external monitor connected.

---

### Post by lads on 2012-02-14
Hi cortman,

I had to tweak that script a bit to make it "work", "work" as in running without errors:

```
#!/bin/bash

var=$(xrandr | grep 'VGA1 connected')

if [ -n "$var" ] ; then
	xrandr --output VGA1 --primary 
	xrandr --output LVDS1 --off 
else
	xrandr --primary LVDS1 
fi
```

This shuts down the internal monitor alright, but the signal sent to the external monitor is on a lower resolution that it supports, making it look really ugly. Opening the monitors menu and trying to change it to the correct resolution I get this error:

```
could not assign CRTCs to outputs:
Trying modes for CRTC 63
CRTC 63: trying mode 1600x900@60Hz with output at 1600x900@60Hz (pass 0)
    none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1680x1050@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1600x1200@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1280x1024@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1280x1024@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1440x900@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1440x900@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1152x864@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1024x768@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1024x768@70Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 832x624@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 800x600@72Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 800x600@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 640x480@73Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 640x480@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 640x480@67Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 720x400@70Hz with output at 1600x900@75Hz (pass 0)
CRTC 63: trying mode 1680x1050@60Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1600x1200@60Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1280x1024@75Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1280x1024@60Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1440x900@75Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1440x900@60Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1152x864@75Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1024x768@75Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1024x768@70Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 1024x768@60Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 832x624@75Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 800x600@72Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 800x600@75Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 640x480@73Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 640x480@75Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 640x480@67Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1600x900@75Hz (pass 1)
CRTC 63: trying mode 720x400@70Hz with output at 1600x900@75Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1680x1050@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1600x1200@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1280x1024@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1280x1024@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1440x900@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1440x900@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1152x864@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1024x768@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1024x768@70Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 832x624@75Hz with output at 1600x900@75Hz (pass 0)
CRTC 64: trying mode 800x600@72Hz with output at 1600x900@75Hz (pass 0)
```

I believe this is all related to the mess up with the Fn+F7 key combination, possibly another unintendend consequence of a kernel update.

Thank you for the help anyway.

---

### Post by cortman on 2012-02-14
Yes, something is definitely wrong with Fn+F7. You may want to downgrade or upgrade the kernel again.

---

### Post by lads on 2012-02-14
Hum, this is getting strange. I had to logg off and when I logged back in the script worked alright. I tried a few other times and the resolution of the external monitor seems to be dictated by the national lottery or some such. A matter of trying till it gets to the right one.

I'll leave this issue open for now since this is just a workaround. The kernel upgrades in the 64-bit version can be a real adventure.

Thank you for the replies.

---

### Post by lads on 2012-02-15
There was another kernel update yesterday. The Fn+F7 key is back at work.

---

