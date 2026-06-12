---
title: "NVIDIA GeForce 520M performance and driver question"
date: 2013-02-22
forum: Hardware
---

### Post by jwaclawsky on 2013-02-22
I just installed Unbuntu 12.10 (32 bit version) on a ZOTAC ZBOX (it has an Intel Atom D2700 dual-core, 2.13 GHz). This machine has an Intel NM10 Express chipset and an NVIDIA GeForce GT 520M GPU (with 512 MB DDR3 memory). 

The problem is the system is running very slow.  The system monitor shows 4 CPUs (I guess that is 4 threads because it is a dual core chip - I am not sure why it thinks 4 threads - perhaps hyper threading means 4 CPUs, maybe someone could explain that to me). All 4 "CPUs" are running &#8220;at least&#8221; 50% to 80% even with the system sitting idle. The "Top" command shows very similar results with compiz thrashing the cpu's. The performance monitor and a terminal screen shot with "top" is shown in the attached pictures. 

What I find confusing is that when I go to software sources - additional drivers. I find 5 drivers listed. The driver choices are shown in the attached screen shot (see attached thumbnails). Does anyone know which of the 5 driver choices. I should be selecting or am I missing the correct driver? Is it ok to just try each driver sequentially to see if the compiz thrashing problem goes away (I am worried I will loose my video feed and get stuck - so I thought I'd ask first). Many thanks for any assistance.

---

### Post by jwaclawsky on 2013-02-22
It was a driver issue. I got over my fear of trying out (applying) the 5 different drivers that were available in software sources - additional drivers. I tried them out by selecting them one at a time to see what they did. When I selected a new setting the system processed for 5 to 10 minutes and I believed the new driver was being activated! But the problem didn't change and this confused me. Finally I realized the driver changes probably won't take effect until I reboot. Once I rebooted, the problem went away. I am still not sure which is the best driver but all I know at this point is that it is NOT the Open source driver. Now the machine is nice and responsive and compiz and xorg are running at approx. 3 to 4%. Still a couple of minor things I am investigating but this is closed. There should be a notice that when you change the driver setting you need to reboot!

---

