---
title: "No tty after installing Nvidia proprietary driver"
date: 2014-03-19
forum: Hardware
---

### Post by thefuture-hightech on 2014-03-19
Hi. First of all, sorry about my bad English.
I've installed Xubuntu 13.10 on my laptop.( Sony Vaio F11GGX/B )
After installing nvidia proprietary driver( version 319 in Additional Drivers ) , I have no tty. In fact They are not visible and I have blank screen in tty 1-6 but tty7 is OK and I can go back to my desktop.

How to fix it?:confused:

I also have this problem in opensuse.:(

I think this Problem is only for  laptop.

---

### Post by thefuture-hightech on 2014-04-05
up...:(

---

### Post by steeldriver on 2014-04-05
I experienced a similar issue with an nvidia-based laptop but I never really found out why

A workaround I used for a while was to re-enable the framebuffer device by commenting out the line in /etc/modprobe.d/blacklist-framebuffer.conf:

```
blacklist nvidiafb
```

HOWEVER I don't think that's the right way to fix it. I kind of suspected it was something to do with the GRUB_GFXMODE but was never able to confirm that. Does your laptop screen have a non-standard aspect ratio (e.g. 16:10 instead of the more usual 16:9)?

FWIW I am now running 319.37 on 12.04 (32-bit) and the ttys work fine (without the framebuffer enabling hack).

---

### Post by thefuture-hightech on 2014-04-05
Thanks for your reply.

commenting out "blacklist nvidiafb" doesn't help :sad:

> Does your laptop screen have a non-standard aspect ratio (e.g. 16:10 instead of the more usual 16:9)?

It's 16:9 :wink:

---

### Post by thefuture-hightech on 2014-04-10
up...:sad:

---

