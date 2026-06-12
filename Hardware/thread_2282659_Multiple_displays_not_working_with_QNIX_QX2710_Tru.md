---
title: "Multiple displays not working with QNIX QX2710 True10"
date: 2015-06-16
forum: Hardware
---

### Post by h3xw0l7 on 2015-06-16
Hello all,

I just ordered two new monitors, two QX2710 monitors for use with my desktop with Linux Mint 17.1 with XFCE4 as my window manager. I found out that one of them is actually a QNIX QX2710 True10 and that particular monitor is not allowing me to use it as a display. When I enable display on the True10 monitor it cycles through colors before finally going back to idle. I started with the default xserver-xorg-video-nouveau driver and eventually moved to using the recommended nvidia-331 driver with no luck. Having read some suggestions on a different forum I went to modify the xorg.conf file only to find it didn't exist under /etc/X11/xorg.conf. A whereis command yielded /usr/lib/xorg and /usr/include/xorg and I wasn't sure which one I would modify if either. Does anyone know how to get this distribution to play nice with this 10 bit monitor?

Thanks in advance!

---

