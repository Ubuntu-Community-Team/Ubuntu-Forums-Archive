---
title: "Performance issue: Acer Travelmate 8473TG"
date: 2011-08-01
forum: Hardware
---

### Post by bjapa on 2011-08-01
I recently installed Ubuntu 10.04 and upgraded to 10.10 and then 11.04 (amd64). Now I'm not at all satisfied with this laptops performance:

When using standard Ubuntu desktop, it takes seconds until menu icons are shown or it takes long until a terminal is available. With Xfce it is a bit better but not yet satifyable. 

Even on console (Alt+Ctrl+Fx, x<7) it took about 15 secs until I had a bash prompt. 

Compared to an older laptop, this is a very bad feeling. 

On the other hand, there are things that look quite positive: etracer runs smooth and has an average of 13 fps. hardinfo has following results: Blowfish 5.3, Cryptohash 242, Fibonacci 2.314, N-Queens 5.314, FFT 1.08, Raytracing 4.697.

I was wondering if this is a CPU frequency problem or an issue with graphics card.

The Laptop has a intel Core i5-2410M 2.3GHz CPU with integrated graphics and the NVIDIA GT540M with Optimus support.

lspci | grep VGA:

0:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

I have no /etc/X11/xorg.conf file.

Any hint on how to resolve this further would be very nice. Thanks in advance.

---

