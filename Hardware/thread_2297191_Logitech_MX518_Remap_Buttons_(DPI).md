---
title: "Logitech MX518 Remap Buttons (DPI)"
date: 2015-10-01
forum: Hardware
---

### Post by ostblocklatino on 2015-10-01
Hello!
First of all : i searched the internet for hours, tried everything i was able to do and also tried solutions from this forum. The problem is that most of the threads and solutions on the net are outdated and dont apply to actual Ubuntu Versions.
So basically the title says it all but i'll just repeat that . I use the Logitech MX518 Optical Gaming Mouse on Linux Mint 17.2 Cinnamon and can't remap or atleast deactivate the DPI Buttons (defined b8, b9 i think). xbindkeys doesnt help atm. But i figured out that the signal by the DPI Buttons isnt received properly ( terminal 'xev' doesnt show anything when they're pressed). BUT if i press them, they DPI does actually change so they do work!
btnx and things like hidpoint are not supported anymore so i thought ill try it on this forum since i was redirected here many times whilst searching for a solution.
I dont even want these buttons to do fancy commands just remap them to a normal hotkey like ' p ' and ' o ' for example so i can use them for example in league of legends.
A windows distro is not a possibility for me..
Thanks in advance

---

### Post by efflandt on 2015-10-02
I don't have any mice that can change dpi (using Logitech MX Master li-ion rechargable). But I imagine that dpi may be something internal to the mouse and how it reports its movement. Games themselves often have a mouse sensitivity setting if a mouse is too responsive or not responsive enough.

There was some discussion in "Steam for Linux" forum in Steam about polling frequency and some people thought it was 125 Hz by default in Linux. But when I checked "lsusb -v" and "sudo cat /sys/kernel/debug/usb/devices" in 64-bit 14.04, my Unifying Receiver was polling my mouse at bInterval 2 or Ivl=2 ms (500 Hz) by default which should be fine for gaming.

---

### Post by ostblocklatino on 2015-10-03
Okay, thanks for your answer :) i think i'll just set up another pc for gaming related stuff etc but maybe this will help someone else

---

