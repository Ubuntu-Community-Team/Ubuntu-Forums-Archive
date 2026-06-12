---
title: "Problems with my FX5200"
date: 2010-09-10
forum: Hardware
---

### Post by Drizak on 2010-09-10
Hi, i have a Nvidia GPU (Evga FX5200 128Mb), and with Envy-NG I have installed the 173.14.20 drivers.. the perfomance of my VGA is pretty bad compared when i was in Windows, most applications wont work in fullscreen (my screen says that resolution isnt supported, when it can display under that mode).. i realized a glxgears and i noticed about this:


```
drizak@drizak-desktop:~$ sudo glxgears -fullscreen
Error: API mismatch: the NVIDIA kernel module has version 173.14.20,
but this NVIDIA driver component has version 173.14.25.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
724 frames in 5.2 seconds
```

Searching for 173.14.25 drivers doesnt leads me into something useful.. so im asking here for help
Thanks, if you need something else please tell me :KS

---

### Post by Drizak on 2010-09-11
bump

---

