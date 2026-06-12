---
title: "sometimes my screen will only refresh the part near my mouse pointer"
date: 2022-03-01
forum: Hardware
---

### Post by sonoichi on 2022-03-01
when it happened, I move my mouse pointer slightly, 
a row of pixel near the pointer got refreshed.
[IMG]https://i.stack.imgur.com/jmVjC.png[/IMG]

about 10s later the whole screen refreshed
[IMG]https://i.stack.imgur.com/Hos0Z.png[/IMG]

I had this problem on ubuntu 21.10, then I upgraded to dev version, who knows the problem also exists, idk what to do

~$ inxi -G
Graphics:
  Device-1: Intel Iris Plus Graphics G1 driver: i915 v: kernel
  Device-2: NVIDIA GP107M [GeForce MX350] driver: nouveau v: kernel
  Device-3: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: wayland server: X.Org v: 1.21.1.4 with: Xwayland v: 22.1.0
    compositor: gnome-shell v: 41.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics (ICL GT1) v: 4.6 Mesa 21.2.6

---

### Post by tea for one on 2022-03-01
```
Device-2: NVIDIA GP107M [GeForce MX350] driver: nouveau v: kernel
```

You are using the open-source nouveau driver for your Nvidia graphics card.
Have you tried to install the proprietary Nvidia drivers?

---

