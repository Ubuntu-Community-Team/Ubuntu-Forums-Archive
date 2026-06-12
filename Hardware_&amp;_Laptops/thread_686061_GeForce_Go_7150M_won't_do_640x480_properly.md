---
title: "GeForce Go 7150M won't do 640x480 properly"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by DontThinkSo on 2008-02-02
Hey all, I have a rather strange bug when setting my widescreen laptop resolution to 640x480...

You see, whenever I try to switch to 640x480 resolution, the bottom part of the screen gets cut off. I know it's still there, because I can still move my mouse off the screen and click things, and rotating my desktop with compiz shows the bars and everything are still there.

xrandr reports the following:

Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0* 
   1024x768       51.0  
   800x600        52.0  
   800x512        53.0  
   720x450        54.0  
   640x512        55.0  
   640x480        56.0     57.0  
   640x400        58.0  
   640x384        59.0  
   512x384        60.0  
   400x300        61.0  
   320x240        62.0  

X appears to be using 640x400 for my physical screen resolution, but 640x480 for my desktop resolution.

In the past, I could switch manually to 640x480 at 57 Hz, which would magically fix the problem. Now, however, it seems something has changed, and neither frequencies will fix the problem.

This is a problem for me because I like to play Starcraft, which normally runs at 640x480. I had it all set up perfectly, with a custom icon and a short script to switch the frequency to 57 Hz 3 seconds after starting Starcraft (which, as I said would fix the resolution issues). Now, this method doesn't appear to work.

Any ideas?

---

### Post by DontThinkSo on 2008-02-03
bump?

Does anyone else have this problem?

---

### Post by clarke-pj on 2008-05-30
I don't suppose you got anywhere with this. I'm having the same problem on my laptop.

Pete

---

