---
title: "Karmic Strange performance issue"
date: 2010-02-26
forum: Hardware
---

### Post by datpapi on 2010-02-26
I recently installed a clean copy of Ubuntu 9.10. I've noticed a strange issue which began with what I thought was just a problem with Compiz fusion.
 
I've installed the latest updates, kernel, and versions of all my applications. Here is the problem.
 
When I first open a program( firefox, nautilus, etc) there is a slight lag before openining. With Compiz, the first time I initiate an effect such as burn or minimize, the animation is slow. If Immediately open a second application window of the same type(ie second firefox window) the response is immediate. With compiz, If I close two windows in quick succession, the effect for the first window is laggy, while the second window is smooth. The smooth performance will continue as long as I repeat an open or close of these programs fairly quick to each other.
 
If I let the computer idle - for about a minute without opening another instance of firefox or having compiz do the burn effect, the first time lag issue occurs again.
 
My initial guess was the GPU scaling as I could see my Nvidia card would jump from 169MHZ(min) to 400MHZ(max) and then throttle down after the applicaion opened or compiz performed the  effect.
 
I turned the scaling off and set it to MAX. Even with this I still see the issue. I've also done the same to the CPU, yet the problem remains.
 
My only other guess would possibly be HDD initiation timing or recalling from swap. 
 
Again, the programs run fine once open with no lag - it's just isolated to the initial opening of an app or the first run of a compiz effect. Im new to linux so I am not too sure what else I could check. 
 
I am running a dual core Centrino VPro CPU based laptop with 4GB of RAM and a 4096MB swap area

---

