---
title: "Graphics support 32-bit and 64-bit?"
date: 2011-07-27
forum: Hardware
---

### Post by SynonM on 2011-07-27
I like using Ubuntu, don't get me wrong, however their native support for my new graphics card kinda sucks. It's a ATI Radeon 2 gig cache I believe. It gets really hot in both 64 bit and 32 bit ubuntu (I thought 64 bit was the problem 1st). Anyway I tried the support driver from the amd site and still it is way too hot.

I don't like the price tag on windows OS's but they are still always support ready...I am not a hardcore techie, but know a thing or two. 

Please any suggestions or help, otherwise I'll wait for better driver support from the GPU company site or Ubuntu xorg repositories. Either way Xorg is the best they got right now for my card and it is too hot especially with Unity enabled.

Funny note... the card is supposed to be 3d acceleration ready... oh well...

this was the problem I get when trying to run Unity from the terminal... 

it all works fine and I notice the bar at the top of the screen changes with integrated windows then suddenly it says

Segmentation Fault

right before the unity launcher bar appears... 

I am pretty sure I can run 2d unity but even in classic mode the card runs hot... not cool... literally 
please helpful suggestions

---

### Post by mastablasta on 2011-07-28
use lspci command in terminal to get the graphics chip on your card, then post it here.

---

### Post by .... on 2011-07-28
The proprietary ati/amd driver doesn't work with Unity. This is a widespread/known issue.

---

### Post by SynonM on 2011-07-28
> **mastablasta said:**
> use lspci command in terminal to get the graphics chip on your card, then post it here.


I am on windows right now and using 'CPU-Z' and 'system information' I found this...


[IMG]http://img695.imageshack.us/img695/4430/st2t.png[/IMG]
[IMG]http://img840.imageshack.us/img840/3565/st1g.png[/IMG]
[IMG]http://img835.imageshack.us/img835/2913/55081721.png[/IMG]

Hope that helps.

---

