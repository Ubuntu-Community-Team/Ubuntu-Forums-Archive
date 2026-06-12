---
title: "SoMagic Easycap clone, Not working."
date: 2013-04-12
forum: Hardware
---

### Post by Cinaed666 on 2013-04-12
Hello,

I have an cheap videocapture usb dongle which I would like to use to capture some screenshots from a super nintendo.
Using lsusb, I identified it as a SoMagic Easycap clone, since it didn't say on the box.
I followed the following guide: [https://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted#Prerequisites](https://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted#Prerequisites)
But this was the result, and I don't know why:
```
kenny-ThinkPad-E520 ~ # lsusbBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 020: ID 1c88:003c Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) [SMI-2021CBE]
Bus 001 Device 017: ID 1241:1603 Belkin Keyboard
Bus 001 Device 015: ID 045e:0773 Microsoft Corp. 
Bus 001 Device 006: ID 5986:03b3 Acer, Inc 
Bus 002 Device 004: ID 147e:1002 Upek 
kenny-ThinkPad-E520 ~ # somagic-init
USB device already initialized
kenny-ThinkPad-E520 ~ # somagic-capture | mplayer -vf yadif,screenshot -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3
Failed to claim device interface: Device or resource busy
Is somagic-capture already running?



```

I don't have the cd anymore, so I googled the firmware, maybe it's that? I also hadn't connected a video source at that point, but I figured it would give me a black screen.

Any idea? Thanks!

---

