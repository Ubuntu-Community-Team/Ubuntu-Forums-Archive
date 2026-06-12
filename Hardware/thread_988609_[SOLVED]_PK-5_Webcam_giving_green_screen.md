---
title: "[SOLVED] PK-5 Webcam giving green screen"
date: 2008-11-20
forum: Hardware
---

### Post by sjbaugh on 2008-11-20
I have recently acquired an A4Tech PK-5 webcam for use primarily with Skype. When I try to use it with Skype, the display is predominately green with a few lines of random pixels. The Chip appears to be a ZC0301P.

I am using 8.10 64bit.

I have tried pre-loading the libraries suggested in the 8.10 known bug fixes sticky but no difference.

Should gspca support this? Is there a way to test this without using Skype?

Thanks,

Steve

---

### Post by Mewshi on 2008-11-20
Try installing cheese; that should work.

---

### Post by sjbaugh on 2008-11-20
Thanks for that. I have installed Cheese and that displays the webcam image OK, which proves that the camera and Linux driver are working, but Skype still gives a predominately green display (which changes a bit occasionally). I have retried the suggested bug fixes but still the same result.

Interestingly, lsusb identifies the camera as a ZC0303 but Skype and cheese displays it as a ZC0301(P).

When I start Skype from a terminal it displays:

```
Skype V4L2: Failed to change capture framerate (15)
Skype V4L2: Failed to change capture framerate (15)
Starting the process...
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280
```

---

### Post by Mewshi on 2008-11-20
It looks like, since it can't get the framerate it wants (15?) it's getting corrupted.  Look into that?

---

### Post by sjbaugh on 2008-11-20
Yes, I suppose the chipset might not support 15fps. I might need a different webcam. My local store stocks a Microsoft webcam. Does anybody know if this works well with Ubuntu?

Steve

---

### Post by sjbaugh on 2008-11-21
I finally got it working! I don't have to fill Microsoft's coffers this time. I found that I needed to do quite a complicated procedure (for me!) that is documented at:

[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

---

