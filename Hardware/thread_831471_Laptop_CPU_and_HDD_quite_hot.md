---
title: "Laptop CPU and HDD quite hot"
date: 2008-06-16
forum: Hardware
---

### Post by waapwoop1 on 2008-06-16
Hi,

I am very new to Ubuntu, i installed 8.04 on my Compaq Evo 610c Laptop. Everthing went really well with the install. 

i thought the laptop was very very hot after the install, so i looked at lm-sensors, which told me my HDd sits on 56-57 degrees C and CPU was sitting on about 55 degrees C.
I changed some setting for the CPU freq and now cpu sits on 45 degrees. However when i have some load n cpu, say youtube video, it goes up to 70 degrees very fast.

This didnt' happen under windows. I think the HDD might be too hot at 57 when the thing isn't being used, and i am worried about my  cpu burning up if its above 70 for too long. Can someone help me?

---

### Post by fx2k05 on 2008-06-26
this is a common problem with evo 610c the heat sink is too close to the harddisk   
getting / or making a base cooler should work keeping the temperatures down

---

### Post by waapwoop1 on 2008-06-27
I have read that too. However it was 10 degrees cooler under XP

---

### Post by alan.clements on 2008-07-20
I have a similar problem on my ACER laptop -- although the same problem continues under windows XP. First, can you change the speed of the processor? If so "on-demand" will allow a much faster cooling on some systems. Also, it may sound stupid but try canned air. With the unit off blow in the exhaust towards the intake. You might be suprised at what comes out!

you may have to add [FONT="Fixedsys"]p4_clockmod[/FONT] to **/etc/modules** to get you cpu throttling to work.

---

