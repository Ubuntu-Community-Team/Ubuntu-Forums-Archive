---
title: "HD v4l2 webcam not streaming in HD"
date: 2014-06-25
forum: Hardware
---

### Post by Zatnaktel on 2014-06-25
Hello, 
I have a HD webcam Defender G-lens  2577 HD720P. On older notebook with Linux Mint 14 it works right, output in 1280×720px, no problem. When i tried webcam on some older PC (Compaq  D510), webcam was streaming in 320×240px. On PC is the same OS and SW. I tried everything and it's still the same.

Command **v4l2-ctl -V -d 0** on notebook:
```
Format Video Capture:
    Width/Height  : 1280/720
    Pixel Format  : 'YUYV'
    Field         : None
    Bytes per Line: 2560
    Size Image    : 1843200
    Colorspace    : Unknown (00000000)
```

And on PC:
```
Format Video Capture:
    Width/Height  : 320/240
    Pixel Format  : 'YUYV'
    Field         : None
    Bytes per Line: 640
    Size Image    : 153600
    Colorspace    : SRGB

```

The same version of kernel, the same drivers. It is possible that this could be caused by hardware?
I really don't know what to do. Any other ideas? 

Thank you so much,
 Zat.

---

