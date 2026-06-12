---
title: "lm-sensors vcore2 temp(1/2/3) and gkrellm"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by benjo316 on 2007-09-16
Just a few questions:

1.) Why is vcore2 constantly at 1.20V(It does change, I've seen it at 1.21V once, but doesn't change often) when Vcore1 scales properly(It drops down to 1.07V when CPU is at 1000MHz).

2.) I would assume "M/B Temp" is incorrect, my reasoning being my computer is not fried(Yet). Am I correct in this assumption?

3.) "CPU Temp" is erratic and often very different from "Core0" and "Core1" temps. I would assume that it is an average of the two, but since it changes so often I'm not sure. What else could it be?

4.) I have no idea what "Temp3" is, anyone have an idea?

5.) GKrellM reports temp1, temp2, and temp3. Am I correct in assuming that they are M/B Temp, CPU Temp, and Temp3?

I think that's about it. I've attached a picture of the output of "sudo sensors". I would also ask why GKrellM does not report the core temps but I believe that when I have compiled it from source previously(Right now I'm using the one from the repositories) it did report them.

If you need any more information feel free to ask.


Hardware:
Biostar GeForce 6100 AM2 motherboard
AMD Athlon(tm) 64 X2 Dual Core Processor 3600+

OS:
Ubuntu 7.04 (Feisty) 64-bit

[ATTACH]43592[/ATTACH]

---

