---
title: "laptop too hot in ubuntu 12.04"
date: 2013-03-31
forum: Hardware
---

### Post by chrex on 2013-03-31
hi all,

My laptop is much more noisy (from the fan) in ubuntu than in windows xp. I'd like to know if there is any way to reduce the noise from the fan.

The fan speed of my laptop is controlled by the BIOS and has 4 levels (0,1,2,3 in order of increasing speed). According to my observation, the fan speed will go to level 1 if CPU >55 degree celsius or GPU>63 degree, and back to level 0 once CPU<42 and GPU<53.

In windows xp, when doing normal web browsing, about 90% of the time it is on level 0 (the lowest one, comfortably quiet), occasionally to level 1 (which is ok for outdoor use, but already noisy for me in room). It will stay at level 0 when idle.

But in Ubuntu 12.04 (unity 2d), it is almost the opposite. Even in idle, about 2/3 of times it will be on level 1. The noise on level 1 is really disturbing me when in room. 

I have checked the temperatures, the problem seems to be with the video card (Nvidia GeForce 7300), here is the comparison regarding GPU between in windows xp and in ubuuntu 12.04:
1. In xp, the GPU can be stabled at around 56 when idle with level 0 fan speed. When it occasionally climbs to 63 during web browsing, level 1 speed is activated and the GPU temperature is reduced to below 53 very quickly and the noise is over.
2. In ubuntu 12.04, however, even in idle, once the level 1 speed fan reduced the GPU to below 53, it will quickly shoot back to 63 and activate level 1 fan speed again. So the time the computer remains at level 0 is quite short in ubuntu which makes it so noisy.

I have tried all (but the experimental beta one) Nvidia driver provided in official repository but no big difference. I also tried turning off x server by 
"sudo service lightdm stop"
but no change in the fan speed.

Any ideas or suggestions are appreciated.

Thank you all.

---

