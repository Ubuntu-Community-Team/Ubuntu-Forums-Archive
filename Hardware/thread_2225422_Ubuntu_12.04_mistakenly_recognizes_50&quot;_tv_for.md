---
title: "Ubuntu 12.04 mistakenly recognizes 50&quot; tv for a 7&quot; device with hdmi"
date: 2014-05-21
forum: Hardware
---

### Post by Jan_Boy on 2014-05-21
Hi

When i connect my samsung tv ( model LE32A552P3R) to my Dell Inspiron 5050 ubuntu starts really to run really slow.

After some searching i found that it recognises my tv as a 7" device needing powe[B]r.
[/B]
xrandr gives me as follows:
##################################
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm


   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+1366+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.0*+
   1280x720       50.0     60.0  
   640x480        60.0  
DP1 disconnected (normal left inverted right x axis y axis)
#######################################
[FONT=Calibri][/FONT]
How do i change this autoconfiguration when plugging in the hdmi? 

(fyi: starting up the laptop with hdmi plugged in does not work)

I have been googling for a solution for some time without finding any solution. Can someone please help?

---

### Post by markosjal on 2014-05-22
I have ran into this before on some boards. I think the trick is to disable the LVDS port and maybe you can do that in BIOS but may have to do that from software. It was over a year ago I ran into that so I do not recall the specifics. As I recall I disabled it with a line or two of text in a config file, as I could not disable it in BIOS

I think the board is probably mirroring the HDMI (or VGA) to the LVDS port. If you are running a GUI and depending on the chips for the video ypou may also be able to disable the LVDS from the display utility

---

