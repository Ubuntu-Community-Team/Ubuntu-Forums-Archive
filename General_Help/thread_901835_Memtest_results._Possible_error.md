---
title: "Memtest results. Possible error?"
date: 2008-08-26
forum: General Help
---

### Post by Sinkingships7 on 2008-08-26
Well, I've been experiencing troubles with data transmission on my computer. Things never seem to transfer anywhere properly. Played some video's off of my iPod on Ubuntu: worked great. Moved the files to my computer from my iPod and tried to play them: glitchy as hell. I can NEVER successfully burn an ISO image. Or if I do, I get input/otuput errors when trying to install the OS, or any OS for that matter. I always have to install the base system and 'sudo aptitude install ubuntu-desktop' after that. Then fix the broken packages.

This all gets VERY frustrating, as it makes using my computer a battle every time.

So I decided to run tests on my hardware to try and pinpoint the culprit, so that I may replace it. I'll have more questions on that in a bit. I was about to go to bed, so I thought I'd just go ahead and run memtest. Well, it came back with 38,000 errors, and no where near that many passes. But everytime I run it, the results are different. Never consistent. For example, the first time I ran it, it immediately spit out thousands of errors. I ran it again right after, and it was fine. this inconsistency is what leads me to believe that it is not my RAM that is at fault, but rather a faulty bus on my motherboard, or my CPU.

As of right now, memtest is the only thing I've done to test my hardware. I've seen reports of people complaining that some processors are at fault for lost data transmissions and whatnot, so I don't want to exclude that possibility.

My Questions:
1.) Can the inconsistency of the results of memtest be because of other faulty hardware, like CPU or motherboard?

2.) What are ways that I can test to see if the fault lies with my motherboard, CPU, or HDD?

3.) Any other suggestions?

4.) As a side debate, I would like to know what companies you trust the most for motherboard manufacturing.


COMPUTER SPECS (self-built)

NVIDIA GeForce 8400GS; support up to 512 MB (256 MB onboard); 64-bit; GDDR2; PCI Express x16; [RETAIL]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127296](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127296)

AMD Athlon 64 X2 4000+ Brisbane; 2.1GHz; Socket AM2; [RETAIL] 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103774](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103774)

2GB (2 x 1GB) 240-Pin DDR2 SDRAM; 800 Mhz (PC2 6400); [RETAIL]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820161030](http://www.newegg.com/Product/Product.aspx?Item=N82E16820161030)

Western Digital HD; 160GB; 7200 RPM; 8MB Cache SATA; 3 Gb/s Hard Drive [OEM]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075)

Acer Black 20" Widescreen LCD Monitor; 2ms(GTG) response time; DVI; [RETAIL]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16824009131](http://www.newegg.com/Product/Product.aspx?Item=N82E16824009131)

Samsung SuperDrive; [OEM]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827151161](http://www.newegg.com/Product/Product.aspx?Item=N82E16827151161)

MSI MoBo; AMD Socket AM2; NVIDIA GeForce 6100; nForce 405 chipset; 2 x 240 PIN DDR2; [RETAIL]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167009](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167009)

---

### Post by LateNiteTV on 2008-08-26
geek squad.

---

### Post by Sinkingships7 on 2008-08-26
> **LateNiteTV said:**
> geek squad.

Will they check my computer for free? What do you know about them? Have you used their services before?

---

### Post by srt4play on 2008-08-26
> **Sinkingships7 said:**
> Will they check my computer for free? What do you know about them? Have you used their services before?

The geek squad comment was meant to be funny not serious.

I would start by removing one of the memory modules and run memtest again. Repeat the process with the other module.

---

### Post by Sinkingships7 on 2008-08-26
> **srt4play said:**
> The geek squad comment was meant to be funny not serious.
Thought so.
> **srt4play said:**
> I would start by removing one of the memory modules and run memtest again. Repeat the process with the other module.
I will try that.

---

### Post by Sinkingships7 on 2008-08-27
Quick bump before bed.

---

