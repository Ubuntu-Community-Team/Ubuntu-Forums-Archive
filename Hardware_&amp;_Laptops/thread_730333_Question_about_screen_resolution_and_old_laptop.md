---
title: "Question about screen resolution and old laptop"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by rumpyhw on 2008-03-20
Hi, I know this is probably a hopeless question but here goes. 

Is there a way to increase the screen resolution of an Acer Travelmate 202T laptop to beyond 800x600?

the video card is an  	

ATI Rage Mobility-M1 with 4MB SDRAM

Yes its an old laptop. My department was tossing them out and well I went dumpster diving. I am trying to make up a computer cart for my classes so that I can use a computer projector and wiimote whiteboard. This laptop would be a nice cost effective (free) way of beginning this project. I just need something basic to run and all I would like to do is boost the resolution. According to the specs of this machine is can support 1600 X 1200 max on an external display. But I do not know how to do this. 

Any advice would be most appreciated.
Chris

---

### Post by overdrank on 2008-03-20
> **rumpyhw said:**
> Hi, I know this is probably a hopeless question but here goes. 

Is there a way to increase the screen resolution of an Acer Travelmate 202T laptop to beyond 800x600?

the video card is an  	

ATI Rage Mobility-M1 with 4MB SDRAM

Yes its an old laptop. My department was tossing them out and well I went dumpster diving. I am trying to make up a computer cart for my classes so that I can use a computer projector and wiimote whiteboard. This laptop would be a nice cost effective (free) way of beginning this project. I just need something basic to run and all I would like to do is boost the resolution. According to the specs of this machine is can support 1600 X 1200 max on an external display. But I do not know how to do this. 

Any advice would be most appreciated.
Chris

Hi and have you tried to reconfigure you xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and what version of Ubuntu are you using?

---

### Post by Yellow Pasque on 2008-03-21
Are you using the ati driver? What does this return?:
```
xrandr -q
```

---

### Post by rumpyhw on 2008-03-21
Thank you for the replies. I ran xrandr -q  still totally new to linux and it gave me a listing of screen resolutions with 800 X 600 being the highest in the list. I suppose this computer is just too old for anything more.

---

