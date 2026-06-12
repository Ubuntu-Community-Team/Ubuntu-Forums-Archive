---
title: "nvidia GTS 250: temperature when idle"
date: 2010-05-24
forum: Hardware
---

### Post by lucesei on 2010-05-24
Hi and straight to the problem:
I have the above card installed and am running lucid 64 bit. I have the latest supported driver installed - 195.36.15.
When idle (meaning doing nothing at all, not even a 3d screensaver), I have an avg. temp. of 64-65 °C with fan speed at 36-37 %. Fan speed adjustment is not supported by the card. This temp. is far too high.
On Win7 its around 43-44 °C - on Sidux it runs around 50-51 °C, high but still OK.
My question obviously is: does anyone have an idea of what is going on? A way of lowering the temp.?
I think this is a hint: on Sidux 64 bit I noticed that when idle the gpu clock runs at 300 Mhz, and goes to 760 Mhz when needed (driver is the same as on Ubuntu). On Ubuntu it always runs at 760 Mhz, even when idle. So this is probably the cause, but why does it not scale frequency?

Thanks a lot for any help and bye

---

### Post by lucesei on 2010-05-25
Update on the problem: what actually doesn't work is the 2D mode. The video card always runs at full 3D speed even when not needed. In fact I also have installed an Ubuntu 9.10 (32 bit) with the same driver. Here everything runs smoothly:
2D - Clock at 300 Mhz, Memory at 100 Mhz - when idle
3D - Clock at 760 Mhz, Memory at 1000 Mhz - when working

In Lucid, the 2D mode gets completely ignored. Maybe someone has an idea as to why? Thanks and bye,

Luca

---

