---
title: "Asus 7300gs and HD TV: resolution issues"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by HgBoy on 2007-08-09
I have connected my 7300 gs to my 27" Olevia HDTV with a DVI-HDMI cable. In the nvidia toolbar page, it says the screen's native resolution is 1360X768. When i set it on this resolution (or any others) there is a small portion of the screen that goes outside the viewing area on the tv. I have had the tv hooked up through a laptop before, and had no such issues. I checked my xorg.conf file, and there is no listing for the 1360X768. Would adding this in fix the problem (at work right now, otherwise i would just try it). The only other thing I can think of would be a driver issue. I think I may be using the nvidia driver for the older geforce cards, which might be the issue with the HD out. Any ideas???

---

### Post by HgBoy on 2007-08-09
Ok, I have the xorg.conf file edited in with the proper resolution, and have the proper nvidia driver installed for my particular card. I still have the screen spilling slightly over the viewing area on the screen. I'm sure this is something simple that i am overlooking. I will attach my xorg.conf file.

---

### Post by tseliot on 2007-08-10
try typing:
```
sudo nvidia-settings
```

and set the resolution from there

---

### Post by HgBoy on 2007-08-13
I have got the resolution set, but I still get the screen going off of the tv. If I connect the tv with a vga cable, it works just fine, but not exactly at Hd quality. Do I need to do anything specific in my xorg file to make the video card use the DVi out as opposed to VGA?

---

### Post by HgBoy on 2007-08-13
Ok, I've been doing some more research and my problem seems to be overscan. About 20 pixels dont show up on the screen around all sides., when in VGA mode, this does not happen. I have not been able to find any specific information regarding my tv, and dont know that much (if anything at all) about mode lines for HDTVs. Can anyone help me create a modeline if I can give some specs on the TV?

---

