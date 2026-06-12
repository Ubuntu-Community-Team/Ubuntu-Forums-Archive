---
title: "xrandr not displaying correct refresh rates"
date: 2008-09-12
forum: Hardware
---

### Post by pteri498 on 2008-09-12
I have a decidedly old video chip in a laptop (ATI Radeon IGP 345M, circa 2005) and I'm trying to get it to play nicely with a new wide-screen monitor.

The external monitor's native resolution is 1440x900 @ 60Hz. Here's the output of xrandr:

```

$ xrandr -q
Screen 0: minimum 320 x 200, current 1440 x 1050, maximum 1440 x 1200
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   59.9  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0  
   1152x720       60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 305mm x 228mm
   1400x1050      60.0*+   60.0  
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

```

As you can see, VGA-0 (my monitor) has a resolution of 1440x900 @ 59.9Hz, as far as Xubuntu is concerned. I need this changed to 60Hz, because  at that refresh rate, my screen flickers awfully with any movement of the mouse.

Is it possible to force the resolution to change to 60Hz?

Thank you.

---

### Post by ladgrove on 2008-12-05
Though this is an old forum, it's still a popular hit in google, and people may still have problems setting up Dual Head display in any flavour of Ubuntu.

After hours(days) of xrandr & xorg.conf frustration with Ubuntu 8.10, I was able to display big screen at a resolution of 3360x1050 but stuck at a refresh rate of 60Hz. This was fine for my 22" screen, but for my 17", it was unusable, and I sought to change it to 75Hz.

All attempts through xorg.conf were useless, and using the ATI Catalyst Control Centre doesn't allow changing of options (For ATI HD4850), and now for the embarrassing part. 

I was able to change the 17" refresh rate to 75Hz by simply using the panel buttons on the front of the screen, purely through hardware. I know this seems simple, and it may not help everybody, but it was an oversight that stumped me for 2 days, so I hope it helps someone if they ever have the same issue.

Cheers.

---

