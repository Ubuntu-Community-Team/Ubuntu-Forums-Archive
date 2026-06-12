---
title: "ATI X1400 graphics acceleration on Ubuntu 9.10"
date: 2009-11-16
forum: Hardware
---

### Post by IulianISI on 2009-11-16
I have a laptop DELL Inspiron 6400 with a ATI X1400 video card.
I've tried different approaches described on several forums but nothing is working properly. Now i have installed on my laptop the Radeon driver and i have some graphical acceleration but is working slow and the resolution is stucked at 1024x768.
I booted from the CD loads and everything worked fine and the ATI graphics acceleration worked really well.
How can i make it work like that on my installed version?

---

### Post by romankuzmik on 2009-11-25
1. try removing /etc/X11/xorg.conf
or
2. you can try my xorg.cfg (see attachment). it uses radeonhd open source driver

---

### Post by eklavyaa on 2009-12-20
I am using the open source ATI driver for x1400 on a Dell E1505 (also known as Dell 6400) . When I run glxgears, the gears move, but when I move the window around, the screen has trails left behind. I have this problem with any application that uses 3D graphics.

I have attached a screenshot of this. Any help with this would be greatly appreciated.

PS: I have done a very extensive search on these forums, but there doesn't seem to be anything out there that addresses this problem.

[IMG]http://i45.tinypic.com/241jj1x.png[/IMG]

---

### Post by WindPower on 2009-12-26
Same here :(

---

### Post by ed_qta on 2010-03-04
Dear romankuzmik,

Since my firt upgrade from 8.04 to Intrepid my ATI X1400 (dell inspiron6400) has been a nigthmare. With 8.04 i was able to play even war3, CivIV, ut2004 and many others 3D soft, but no more with 8.10. 

Jaunty and Karmic didn't show any improve about this. The ATI driver simply is NOT compatible with the new kernel, and there was no hope but using XP :(

I have tried with countless solution in many forums, but non of them has worked for my. Either my resolution get stuck in 1024, or the graphic mode did not run at all, so my only choice was deleting xorg.conf and using the MESA driver as it installs for the first time on 9.10. This means no 3d accel, or whatsoever. 
Not even a youtube Fullscreen video or HD is displayed correctly.

But today i got your advice and your solution, and i must say THANKS because is the first real improve i had on my video since the days of 8.10.

Installing radeonhd from the source ([https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)) and then using your XORG.conf file, allows me now to play HD movies on totem or firefox or googlechrome.

I have been using ubuntu two years ago, reading a lot of forums, but I must say that this has been the best solution to this thread i have ever seen.

---

### Post by jonny2112 on 2010-04-06
Hi, 

I just tried to follow the instructions listed in this thread on me insperon e1505 (its basically the same as the insperon 6400) and now all video playback is very choppy and virtually unwatchable. Is there any way I could revert back to the original graphics driver, or did I just make a wrong turn following the instructions. 
Thanks for you time

---

