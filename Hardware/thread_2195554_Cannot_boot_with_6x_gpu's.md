---
title: "Cannot boot with 6x gpu's"
date: 2013-12-24
forum: Hardware
---

### Post by lolek12345 on 2013-12-24
Hi, 

somehow I did managed to boot ubuntu with 5x gpu's. With a lot of pain and much more time..
I'm having problem with the six one.  On HDD I have win and ubuntu (dual boot), I can get in windws with 6 gpu's with no problem, device manag. recognized it all (2 with exclamation mark- this is not important). When I tried to boot in ubuntu with 6x gpu's, first I selected it, and then wait OS for loading, but it stops/freeze (purple screen) (I think, I waited like 5min, nothing happened-moved). 
When trying with 5 gpus, works immediately. I think there's some trick, with ubuntu or bios. 

Specs: 
-Ubuntu 12.04.3 LTS 64bit
-mobo: GA-990FXA-UD7 (bios updated)
-8GB RAM
-AMD Sempron 145
-6x R9 290 (all on pcie riser) (just one have monitor (dvi-d cable)) Driver: Catalyst 13.12 Linux

I would appreciate any help.
Thank you.

---

### Post by Werne on 2013-12-25
Either you're trolling or you have no idea what you're doing. A single-core Sempron and 6xR9 290, that's not even a gaming machine, it's an insanely mis-configured build...

However, I've seen crazier. :D Assuming you're not messing with everyone here and you paid for those cards, then you ain't gonna like what I'm about to tell you. So without further ado...

Your problems arise from hardware limitations, AMD 990 chipset only supports 4-way Crossfire setups, you have 4 graphics cards in CF and 2 that can't even be utilized due to a chipset limitation. Put simply - you only have 4 active graphics cards in your crossfire setup, the other two are just sitting there on idle since the chipset can't use them along with the other four. You can use all 6 if unlinked, but not in crossfire. Be it Windows, Linux, UNIX, DOS, there is no way in hell you can utilize all six of them in crossfire - it's not a software problem, the mobo won't let you do it, and I highly doubt there is a chipset out in the market that allows for a 6-way CF/SLI.

It's the same as those 970 boards with four PCI-E slots where you can only  have a 2-way CF, put 4 and and only two are utilized due to chipset  limitations.

Regardless of the obvious, even if they were to work, taking into consideration the insanely bad cooling and temps of R9 290 series, along with translating CF scaling performance from 2/3/4-way, and a single-core Sempron - your current setup would have performance so bad that my FX 8320 and Radeon 7770 would run big (and very fast) circles around it.:p

---

### Post by lolek12345 on 2013-12-25
> **Werne said:**
> Either you're trolling or you have no idea what you're doing. A single-core Sempron and 6xR9 290, that's not even a gaming machine, it's an insanely mis-configured build...

However, I've seen crazier. :D Assuming you're not messing with everyone here and you paid for those cards, then you ain't gonna like what I'm about to tell you. So without further ado...

Your problems arise from hardware limitations, AMD 990 chipset only supports 4-way Crossfire setups, you have 4 graphics cards in CF and 2 that can't even be utilized due to a chipset limitation. Put simply - you only have 4 active graphics cards in your crossfire setup, the other two are just sitting there on idle since the chipset can't use them along with the other four. You can use all 6 if unlinked, but not in crossfire. Be it Windows, Linux, UNIX, DOS, there is no way in hell you can utilize all six of them in crossfire - it's not a software problem, the mobo won't let you do it, and I highly doubt there is a chipset out in the market that allows for a 6-way CF/SLI.

It's the same as those 970 boards with four PCI-E slots where you can only  have a 2-way CF, put 4 and and only two are utilized due to chipset  limitations.

Regardless of the obvious, even if they were to work, taking into consideration the insanely bad cooling and temps of R9 290 series, along with translating CF scaling performance from 2/3/4-way, and a single-core Sempron - your current setup would have performance so bad that my FX 8320 and Radeon 7770 would run big (and very fast) circles around it.:p

Have you ever heard of mining gpu. ;)

thanks

---

### Post by Werne on 2013-12-25
> **lolek12345 said:**
> Have you ever heard of mining gpu. ;)
I have, and I mined for Bitcoins on an old Radeon 5770 for a while, but I mine no longer. You on the other hand didn't do your research well - GPU mining became inefficient a while ago. Nowadays you need ASIC hardware for mining, GPU mining is no longer profitable regardless of hardware, you lose more than you gain.

Take the cost of power draw of that rig of yours (6 x 300W = 1800W) and think long and hard how long it would take to mine enough to cover the costs of both your hardware and it's power draw - R9 290 retails at ~450-500$ so that's 3000$ just on the GPUs, I think PSUs to power those would cost an additional 500$ if you don't want to kill the cards with rippling, then another 250$ on the mobo+RAM+CPU, and I'd say some 350$ on a case capable of cooling them enough to perform at an optimal temperature. Count in additional costs like aftermarket GPU cooling (AC Accelero III is 75$ x 6 = 450$) since heat slows down the graphics card processor below it's manufacturer-advertised performance and it draws more power to compensate, and CPU aftermarket cooling unless you want your mining rig to freeze after 20 minutes due to CPU shutting down (let's say another 50$) and fans powerful enough to keep the GPUs cool, which I'd say comes to another 400$ at best.

So as a minimum, you have to cover an initial cost of 5000$ just to have the machine performing at all, water cooling GPU blocks cost 250$ each if you opt for water cooling, and that's without a radiator and pump. Then comes the electricity bill (1296KW/h per month with 0-24 work cycle) and I'm not sure how much it costs since the prices are different around the globe. Going with Croatian prices, that machine would use up ~250$ of electricity per month. 

You'd have to mine ~0.5 Bitcoins per month to cover the cost of electricity, and you'd be left with 85$. Assuming the mining rate is constant and the gain is 0.5 Bitcons per month (and the rate is not constant, but let's assume, the only way you get 0.5 a month with the current difficulty which is only rising is if you're a magician), it would take you about 5 years to break even. But that all depends on difficulty and that's only assuming you don't have any additional costs and that the machine never stops working, and you have to disassemble it to clean it out every now and then, which would take a few hours at best.

Hence why I gave up on it, I got some good money back in the day because I mined when Bitcoins were a piece of cake to mine and they were practically worthless, but they became worth money and I gained some 20,000$ out of them, which is why I now have a house. Right now with difficulty being raised lightning fast and with the inefficiency or post-5xxx series, my guess is you'll never break even, not without investing some $4K into ASICs.

A fair warning though - don't let it get into your head, I know some guys who lost everything because of these kinds of investments into mining. People seem to think mining is easy money overnight and they realize they can't break even after their house gets taken away. I still eyeball the Bitcoin market, but there's no way I'd try mining again, too risky.

---

### Post by lolek12345 on 2013-12-25
Fully agree with you. Mining BTC/Bitcoins with gpu is no longer profitable. :)
That's why I am mining other coin, that you can only mine with gpu (algorithm=scrypt) and no special stuff like Asic.
And the profit of that is much more, like 5x or even 30x more that I would mined with BTC/Bitcoins.

So.. I have still the same problem. 
I tried to boot other version of ubuntu(older-newer(10, 11, 12, 13)) but is the same still hangs when tried to boot(flashing underscore).
Don't know what to do :S  

thanks

---

