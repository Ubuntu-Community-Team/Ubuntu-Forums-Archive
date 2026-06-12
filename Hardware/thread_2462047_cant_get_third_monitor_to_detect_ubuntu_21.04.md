---
title: "cant get third monitor to detect ubuntu 21.04"
date: 2021-05-12
forum: Hardware
---

### Post by devdlp on 2021-05-12
Im using Ubuntu 21.04 and just love it its awesome got everything working properly but i added a third monitor
and the green light comes on on the monitor but no display. In display settings it doesnt show tho. Im using dvi in my on board i have my first and second in the gpu. maybe something to use integrated graphics? Im not sure 
and help would be appreciated.
im also running a msi motherboard dont know if that helps, just saying becuase i think theres in option in bios to turn on integrated graphics

---

### Post by devdlp on 2021-05-15
so does this mean you cant get a third monitor to work in ubuntu 21.04??

---

### Post by Autodave on 2021-05-15
Generally speaking, once you install a graphics card, your internal graphics are disabled.  On VERY rare occasions there may be an option in the BIOS to enable both.

---

### Post by devdlp on 2021-05-21
yea i actually just moved to kubuntu 20.04 and all three work fine now, thnx

---

### Post by devdlp on 2021-07-15
i have the third monitor on now but its twitching and stuff how do i get it right is there a command or something please help

---

### Post by Autodave on 2021-07-15
If you still have it plugged into the onboard graphics, that is likley your problem and you are not going to fix it.

---

### Post by devdlp on 2021-07-15
no its plugged into the gpu by dvi

---

### Post by QIII on 2021-07-15
So you have all three connected to your GPU?  Does your GPU support that?  Some may have several heads, but can't use them all at the same time.

What is the make and model of the GPU?

---

### Post by devdlp on 2021-07-15
nvidia gefore gtx 1060 3gb and yes it works with all 3 out of the box on windows.
Now it goes off and back on im not saure of what to do

---

### Post by devdlp on 2021-07-15
i saw something about twinview would that be something to use?

---

### Post by cryptearth on 2021-07-15
If it works on windows the GPU itself seems able to handle it. As there several types of different 1060 3gb it may help if you could specify the vendor and model you got.
Also helpful: What ports the gpu has and how your monitors connected to it (what type of connectors on both ends - if they'Re differnt: do you use active or passive converters?). What resolution do you try to drive? 1080? 1440? 4k? What refresh rate? 60hz, more?
3GB VRAM is not that much - if you try to drive to much with that you may run into bottlenecks.
What driver do you use? nouveau? nvidia? what version?
You wrote it worked fine after switching to KDE - do you still use KDE or have you switched back to another wdm?

---

### Post by devdlp on 2021-07-15
nvidia 465 driver its a evga 1060 3gb. im on ubuntu 20.04 right now. also one hdmi both sides my main monitor. second one is hdmi to not the big vga into gpu the tird that not working is vga to dvi.
both of the last two have hard phisical converters. im going to put in my other gpu and see what happens

---

### Post by devdlp on 2021-07-15
i plugged in my 1050 ti and they all work now problem solved

---

