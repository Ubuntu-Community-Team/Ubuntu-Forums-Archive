---
title: "Will nvidia work after increase of ram?"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by kaspar_silas on 2009-09-18
Hi guys,

Currently I am running 64bit Jaunty on a dell optiplex 755 with 2x1Gb RAM. The plan is to go to 6Gb. 
Also installed is a 1Gb Nvidia card. The GeForce 6200 rev a1 to be precise. (I am using the recommended Nvidia 180 driver.)

The last time I added RAM on a similar computer it wouldn't boot up and stuck me in a very irritating fail_on_reboot->Install_driver->reboot loop. For the long version of this story see here:
[http://ubuntuforums.org/showthread.php?t=990685]("http://ubuntuforums.org/showthread.php?t=990685")
The short version is that it was due to the nvidia driver not mapping the PCI outside of the 32-bit range. The only solution was to remove the video card or ram. 

However that was on both the previous versions of the nvidia driver and ubuntu. Is this likely to be solved now or will I be just wasting money on RAM?

Any help or suggestions are very greatly appreciated.

---

### Post by presence1960 on 2009-09-18
> **kaspar_silas said:**
> Hi guys,

Currently I am running 64bit Jaunty on a dell optiplex 755 with 2x1Gb RAM. The plan is to go to 6Gb. 
Also installed is a 1Gb Nvidia card. The GeForce 6200 rev a1 to be precise. (I am using the recommended Nvidia 180 driver.)

The last time I added RAM on a similar computer it wouldn't boot up and stuck me in a very irritating fail_on_reboot->Install_driver->reboot loop. For the long version of this story see here:
[http://ubuntuforums.org/showthread.php?t=990685]("http://ubuntuforums.org/showthread.php?t=990685")
The short version is that it was due to the nvidia driver not mapping the PCI outside of the 32-bit range. The only solution was to remove the video card or ram. 

However that was on both the previous versions of the nvidia driver and ubuntu. Is this likely to be solved now or will I be just wasting money on RAM?

Any help or suggestions are very greatly appreciated.

I didn't look at the long version, but you are never wasting money on RAM unless 1) your mobo won't handle the amount you are adding, 2) it is the wrong type of RAM or 3) you really don't need the RAM you are adding.

Buy the RAM if you really need it and remove the vid card. You have to have the case open anyway to put the RAM into the bay(s) or slot(s). So kill 2 birds with one stone.

---

### Post by LowSky on 2009-09-18
I've never heard of this problem before. Try upgrading to the nvidia 185 driver

[http://www.nvidia.com/object/linux_display_amd64_185.18.36.html](http://www.nvidia.com/object/linux_display_amd64_185.18.36.html)

Also 9.10 will be out soon, it will be using a new kernel so that might help too

---

### Post by kaspar_silas on 2009-09-21
Cheers guys,

The ram is ordered. I will naturally blame any problems entirely on you two :) 

Incidentally the problem is (or hopefully was) only a software and specifcally a linux/Nvdia-Driver thing. When I borrowed XP to test it handled the extra RAM fine. So hopefully if the RAM does ruin the system the new kernel will sort it out.

Presence1960 the mobo will handle 8Gb so that is no problem. The issues are if I remove the video card I have only one display output and so drop to a single screen. Which after years of multiscreens ruins my work rate. 

Secondly and more imprtantly I am writing programs in CUDA so I need the GPU to properly test them.

---

### Post by kaspar_silas on 2009-12-04
Just to update for anyone who stumbles across this and wonders if it will be a problem. Basically it won't be the extra RAM worked perfectly.  

So cheers to who ever the person was who wrote the NVIDIA driver or Ubuntu part who solved this.

---

