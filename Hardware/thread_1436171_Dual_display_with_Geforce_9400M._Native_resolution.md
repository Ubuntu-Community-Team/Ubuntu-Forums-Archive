---
title: "Dual display with Geforce 9400M. Native resolution not available"
date: 2010-03-22
forum: Hardware
---

### Post by cyberco on 2010-03-22
I am running Ubuntu 9.10 on my Macbook Air, which has a Nvidia Geforce 9400M videocard. I am using the restricted driver (185).

The problem is that I can use my Dell WFP2408WFP as external display but only with a resolution of 1600x1200 and not its native 1920x1200 resolution (which the Macbook Air does support).

I am using the Nvidia tool for setting display settings, but the strange thing is that under the 'GPU' section the Dell display is said to have:

native resolution: 1920x1200 
best fit resolution: 1920x1200 
frontend resolution: 1600x1200 
backend resolution: 1920x1200 

Why is it using the 1600x1200 resolution and is there a way I can change it?

---

### Post by cyberco on 2010-03-25
UPDATE:
I installed Nvidia's 1.90 driver from here:
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

That solved my problem, I now have 1920x1200 on the external display.

---

