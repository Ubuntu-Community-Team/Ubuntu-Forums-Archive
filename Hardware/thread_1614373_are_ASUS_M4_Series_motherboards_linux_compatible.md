---
title: "are ASUS M4 Series motherboards linux compatible?"
date: 2010-11-05
forum: Hardware
---

### Post by ublintu on 2010-11-05
Hi,

In the near future I want to build a desktop PC and at the moment I'm searching for a fully linux compatible motherboard. I want to use AMD CPU. The motherboard should be 6 core ready and able to use DDR3 memory (or DDR2, but DDR3 preferred).
Here are the possible motherboards from this page:
[http://event.asus.com/mb/2010/m4_6cores/](http://event.asus.com/mb/2010/m4_6cores/)

M4A89GTD PRO                            AMD® 890GX/SB850
M4A89GTD PRO/USB3          AMD® 890GX/SB850
M4N72-E                                                NVIDIA nForce® 750a SLI
M4N82 DELUXE                               NVIDIA nForce® 980a SLI with NVIDIA NVCC and ESA support
M4N75TD                            NVIDIA nForce® 750a SLI®
                                         Supports NVIDIA Clock Calibration(NVCC) function
M4N98TD EVO                                NVIDIA nForce® 980a SLI 
                                 Supports                             NVIDIA Clock Calibration(NVCC) function
M4A79 Deluxe                      AMD® 790FX/SB750
M4A79T Deluxe                              AMD® 790FX/SB750
M4A78T-E                                              AMD® 790GX/SB750
M4A78-E                    AMD® 790GX/SB750
M4A78-E SE                AMD® 790GX/SB750
M4A785TD-V EVO        AMD® 785G/SB710
M4A785TD-M EVO       AMD® 785G/SB710
M4A785D-M PRO         AMD® 785G/SB710
M4A785T-M                AMD® 785G/SB710
M4A785-M                  AMD® 785G/SB710
M4A785G HTPC           AMD® 785G/SB710
M4A78-EM                  AMD® 780G/SB700
M4A78LT-M LE            AMD® 760G/SB710
M4A78L-M                  AMD® 760G/SB710
M4A78 PLUS               AMD® 770/SB700
M4A77TD PRO            AMD® 770/SB710
M4A77TD                   AMD® 770/SB710
M4A77D                     AMD® 770/SB710
M4A77T                     AMD® 770/SB710
M4A77                       AMD® 770/SB710
M4N78 SE                  NVIDIA nForce® 720D
M4N68T PRO              NVIDIA nForce® 630a
M2N68 PLUS               NVIDIA nForce® 630a
M3N78-VM                  NVIDIA GeForce® 8200
M4N78-AM                  NVIDIA GeForce® 8200
M4N78-AM V2             NVIDIA GeForce® 8200
M2N68-AM SE2           NVIDIA Geforce® 7025/nForce 630a
M4N68T-M                  NVIDIA Geforce® 7025/nForce 630a
M4N68T-M LE              NVIDIA Geforce® 7025/nForce 630a
M2N68-AM PLUS          NVIDIA Geforce® 7025/nForce 630a

I searched for compatible lists and I found them, but I always find someone on the internet who had some problem.
+ I found "Linux Status Report For ASUS Desktop Motherboard" in here:
[http://fr.asus.com/websites/global/aboutasus/OS/Linux.pdf](http://fr.asus.com/websites/global/aboutasus/OS/Linux.pdf)
What do you think. Is this list reliable?

**Do you have any experience with any of those motherboards which are listed above?**

I feel like it's an endless searching because I can always find new informations...

---

### Post by ublintu on 2010-11-05
other interesting page:
[http://wize.com/motherboards/brand/asus/t9757-linux](http://wize.com/motherboards/brand/asus/t9757-linux)

M4A785TD-V EVO   has the same chipset like in here:
[http://www.phoronix.com/scan.php?page=article&item=ecs_785g&num=7](http://www.phoronix.com/scan.php?page=article&item=ecs_785g&num=7)
AMD 785G/SB710

Any experience with M4A89GTD PRO/USB3? It looks ok:
[http://www.linuxquestions.org/questions/linux-hardware-18/m4a89gtd-pro-usb3-motherboard-support-829254/](http://www.linuxquestions.org/questions/linux-hardware-18/m4a89gtd-pro-usb3-motherboard-support-829254/)
[http://www.linuxquestions.org/questions/linux-hardware-18/mobo-asus-m4a87td-usb3-anyone-made-the-jump-yet-817435/](http://www.linuxquestions.org/questions/linux-hardware-18/mobo-asus-m4a87td-usb3-anyone-made-the-jump-yet-817435/)

---

### Post by cascade9 on 2010-11-06
That list is pretty old now, and the AMD 7XX (790FX, 790X, 770, 785G, 780G and 760G) chipsets are....well, not quite 'obsolete' but outclassed by the newer 8XX chipsets. 

Theres only 4-5 chipsets that you should be looking at for a Phenom II X6- AMD870+SB850, AMD 890FX+SB850, AMD 880+SB850, AMD890GX+SB850 or possibly on the the nvidia chipset (750a, 780a, 980a). 

I'd go for an AMD chipset, IMO they are better than the nvidia chipsets (the only rweason to get an nVidia chipset AM3 motherobard is if you want to use nVidia onbaord graphics, or run SLI without a hack). 

880+SB850 and 890GX+SB850- onboard video. If your planning on running a  video card (I would!) then dont bother with these. 

870+SB850 and 890FX+SB850- no onboard video. The 870 chipset is solid,and works well. The more expensive 890FX motherbaords are good if yuo want the absolute maximum possible overclock, want the ability to run 3x crossfire (not that many people at all need, or even want this) or if your after the maximum amount of 'stuff' (like eSATA ports, firewire, etc.). 

I'd go for the 870+SB850 is your not planning on overclocking. 

BTW, does it have to be asus? I've seen a fair few of the AMD 7XX and AMD 8XX chipset asus boards, IMO they arent as good as the gigabyte boards.

---

### Post by ublintu on 2010-11-06
Thank you for your really good answer!
So just 3 left: [http://www.asus.com/ProductGroup2.aspx?PG_ID=mKyCKlQ4oSEtSu5m](http://www.asus.com/ProductGroup2.aspx?PG_ID=mKyCKlQ4oSEtSu5m)
M4A87TD
M4A87TD EVO
M4A87TD/USB3

I was searching for gigabyte motherboards, but I couldn't find "any" linux list about new motherboards, just about older.
Now I searched for the same chipset, 870+SB850 and I found this one: [http://www.gigabyte.com/products/product-page.aspx?pid=3517#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3517#ov)
**GA-870A-UD3 **                (rev. 2.1)
mmm better.
Do you have any opinion about this one?

---

### Post by cascade9 on 2010-11-07
If you were going to get an asus 870 motherboard, go for the M4A87TD EVO, its the best of them.

I much perfer the gigabyte GA-870A-UD3. I could gfo on about it, but its easier to just have a look here- 

[http://www.xbitlabs.com/articles/mainboards/display/amd-870-roundup.html](http://www.xbitlabs.com/articles/mainboards/display/amd-870-roundup.html)

---

### Post by ublintu on 2010-11-07
...and the winner is... GA-870A-UD3
This article was helpful to make the decision. Thank you for your great help. A few weeks or month later, when I will first turn the new computer on, I will post the results here.

---

### Post by cascade9 on 2010-11-08
No problem, good luck on your build ;)

---

### Post by ublintu on 2010-11-11
Before I order it, I have an other question.

What's the difference between GA-870A-UD3 (rev. 2.1) and GA-870A-UD3 (rev. 2.0)?
What's the difference between GA-880GA-UD3H (rev. 2.x) and GA-880GA-UD3H (rev. 2.0)?
I saw in the article, the differences what they found are DIMM slots layout and two microchips are missing. I compared rev. 2.1 and 2.0 in Gigabyte homepage, but they didn't show any difference between them. Do you know more about this?
Thank you

EDIT (I got an answer from Gigabyte forum): [http://forum.giga-byte.co.uk/index.php/topic,3437.0.html](http://forum.giga-byte.co.uk/index.php/topic,3437.0.html) 
"The CPB chip stands for Core Performance Boost and as far as I remember  it was for unlocking the extra locked cores on some chips, however  Gigabyte decided it could be done via software instead and so the chips  vanished."

---

### Post by cascade9 on 2010-11-12
I wouldnt be suprised if the version 2.1 (GA-870) or 2.x (GA-880) had different northbridge/southbridge revisions as well. Without actually pulling the heatsinks and looking (or finding a review from somebody who has already) there is no way to know. 

BTW, from what is being said already AMD 8XX chipsets wont run bulldozer. We wont know that for sure untill bulldozer is released. 

Bulldozer is meant to be using the same physical socket as AM2/AM2+/AM3, possibly with different pinouts. (even though it hasnt got an offical name as yet, lets just call it AM3+ to save on typing). AMD has been saying that current AM3 CPUs should run in AM3+ motherboards, but AM3+ CPUs wont run in AM3 motheroboards.

---

### Post by ublintu on 2010-11-16
... and I got the official answer from Gigabyte:

"Rev2.0 and rev2.1 have slightly difference of their hardware design.
 Rev2.1 has better memory OC stability.
 You can check the memory support list."

just to document it. Maybe someone else searching for this information...

---

