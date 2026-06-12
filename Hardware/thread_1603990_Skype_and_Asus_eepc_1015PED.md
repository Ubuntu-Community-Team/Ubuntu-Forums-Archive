---
title: "Skype and Asus eepc 1015PED"
date: 2010-10-23
forum: Hardware
---

### Post by whyster on 2010-10-23
I just got my Asus eepc 1015PED the other day, got sick of windows 7 starer so i installed Ubuntu 10.10 Netbook edition. Im mainly using my netbook for skype and for some strange reason after installing the latest version of skype beta for linux (Version 2.1.0.81) I cant view the video of the person im talking to nor can i see my own video, but the person im chatting with see's everything just fine. Are there any fix's or will I have to wait until the next version of skype for linux?

thanks.

---

### Post by whyster on 2010-10-25
fixed it, just gotta open skype with this command

```
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by 0x656b694d on 2010-11-12
Hello whyster,
how does wifi work on your netbook? Can it see wireless networks around?
How does the touchpad work?

Trying to figure out in which problems i'll run if buy 1015PED for myself.

thanks.

---

