---
title: "Dell Studio Shuts Down When Hot"
date: 2011-03-24
forum: Hardware
---

### Post by diamanthunden on 2011-03-24
Hi i have a Dell Studio 14.

When i run heavy simulations, my laptop gets hot, and suddenly shuts down. I run Ubuntu 10.10.

I can't believe it has to be this way, i get no warning or nothing, the laptop just dies. I think it's because it's too hot, as it does get very hot. 

Any suggestions to what happens and how this can be avoided?

Thanks :)

Ben

---

### Post by TBABill on 2011-03-24
That's an action of the computer itself, not the OS. You have sensors on your motherboard that detect temps and take actions when necessary to try to protect your machine. The fix is to find out why it's getting so hot. Do you have a video card using an open source driver? If so, is there a proprietary driver that can scale your GPU better? Could the airway(s) be obstructed? Is your machine still using CPU Freq Scaling of ondemand as set by the OS when installed?
 
Lots of things can cause heat and you'd need to find the source.

---

### Post by diamanthunden on 2011-03-28
Thanks!

No, the airways are not obstructed. The video card uses a proprietary ATI/AMD FGLRX graphics driver, but i dont think its due to that, since it only overheats when i run heavy computations, that dont show anything visually, just uses the CPUs. 

I have not looked into the freq scaling. 

But shouldn't the computer be able to handle working without downscaling the frequency?

Thanks again,
Ben

---

### Post by TBABill on 2011-03-28
It downscales because at full throttle constantly your processor is cycling about double what it needs to be, creating unnecessary power consumption and heat. However, proper fan and sensor operation should be able to manage cooling the machine properly without it hitting its limits under 'regular' usage. I can't imagine any action so heavy that it would just overheat a machine like that without some hardware or software piece not working properly. My first concern would be my fans throttling and running at appropriate speeds, heat sinks still adhered properly to chips, etc. Anything having to do with heat could cause it to get unnecessarily high and it could be that you need a better heatsink or fan because you use more intensive programs. If it works fine under Windows but not Ubuntu, then it's an altogether different problem related to the OS and how the machine hardware interacts with it.

---

