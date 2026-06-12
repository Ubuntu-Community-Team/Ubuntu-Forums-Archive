---
title: "Deltaco TB-223 keyboard not working, trackball ok"
date: 2010-12-18
forum: Hardware
---

### Post by metu71 on 2010-12-18
Hi,

I bought keyboard trackball combo mentioned in the header. I have not managed to get the keyboard to respond in any way. Trackball is working ok, but any of the buttons don't react in any way. I'm using different versions of Ubuntu in several machines, but the keyboard is not working in any of those. I have tried Ubuntu 9.04 and 10.04.

I have checked from kernel log that both input devices are recognized, but only the trackball is generating events when monitored with xev.

Also using cat on keyboard devices under /dev/input/by-id doesn't produce any output.

I would value hints or ideas what to check and of course if fix is available that would be the best.

---

### Post by metu71 on 2010-12-28
Found the solution, actually it was my neighbor who found it. He tried the keyboard on Windows7 and saw the same problem, then he removed the batteries and put them back and everything was working. I guess keyboard part of the device was in some strange state. This could be result of low battery voltage when I first unpacked it and took into use without first charging it.

---

