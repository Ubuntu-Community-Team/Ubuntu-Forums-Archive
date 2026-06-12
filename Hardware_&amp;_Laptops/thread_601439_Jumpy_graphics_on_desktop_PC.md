---
title: "Jumpy graphics on desktop PC"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by IMOC on 2007-11-03
I installed Ubuntu 7.04 on my old desktop and it all went pretty well apart from a small problem with the display.  If I move windows around it is very jumpy, the same happens if I scroll the content of a window or try to watch any video content.

After much searcing of the forum I found this question had been asked a few times but I could find no answer.  Anyway, some details of my PC:

Packard Bell iMedia
CPU: 2.8GHz P3
Memory: 448 MB DDR333
Onboard graphics with 64MB shared memory

Other posts have suggested that the following is tried:
> 
$ glxgears
822 frames in 5.4 seconds = 151.831 FPS
791 frames in 5.5 seconds = 144.276 FPS
791 frames in 5.5 seconds = 142.632 FPS
791 frames in 5.4 seconds = 146.037 FPS
(Small window showing the gears is shown also)


> 
$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

Does anyone have any ideas how to proceed from here?
Thanks.

---

### Post by mrvertigo on 2007-11-03
I would need to know what kind of onboard graphics nvidia? ATI? intel? ect

---

### Post by IMOC on 2007-11-03
I could not figure out what type of graphics chip was on the mother board so I tried another plan of action.

I went down to PC World and bought the cheapest AGP graphics card they had, which was a GeForce 6200.  Plugged it in, ran the restricted drivers manger, rebooted and just like magic everything now works perfectly.

So my problem is solved now, but thanks for taking the time to respond to my original message anyway.

---

