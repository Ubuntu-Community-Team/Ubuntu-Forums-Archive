---
title: "CPU upgrade"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by tintix on 2007-02-27
**Hi there! I'm looking for a CPU upgrade advice.**

Have a Intel Celeron D (2.53GHz) on a Biostar P4M800-M7A motherboard with 768MB DDR1 RAM (400MHz or PC3200). I'm using Kubuntu Edgy.
Don't wanna upgrade to DDR2 within 1.5 years - so far. But the Celeron D is really annoying. Haven't much money (can afford one for about $140) so I wanna switch to a Pentium D CPU.  But I don't  know which model would be reasonable for my PC? Will my DDR1 slow down the new dual core CPU (I mean, It won't use it's all resources) or there won't be any difference (the PC will be fastes then with previous CPU)?
What about gaming. Will the 2 cores be better for faster 3D rendering? Have a GeForce FX5200.

---

### Post by igknighted on 2007-02-27
I doubt that your CPU is what is dragging your system down.  If gaming is important, the first thing you need to upgrade is you vid card.  Second I would get more RAM.  Unfortunately, DDR1 ram and older AGP type vid cards are more expensive these days than the newer stuff.  I just purchased (am waiting for delivery) of a new CPU/Mobo (Athlon64 X2, 65nm), 1gb dual channel DDR2 ram, and an nvidia 6600gt pcie.. all of which I got from newegg for 300.  SO in the end, it might be in you best interest to wait until you can go to a newer mobo/ram/gfx card (pcie).

---

### Post by Daveth on 2007-02-28
yes, I agree with Igknighted, your gpu will struggle to render even moderatley new cards and will curl up and die at some of the newer ones. However, the AGP bus on your motherboard will not have reached data saturation so you can still use that. For a nvidia card I would go no lower than a AGP 6600gt, which you may be able to pick up cheap now that the rest of the world has moved to the pcie bus- precious few are made anew now (if any- not checked for some months). Then put as much ram as you can afford in - 2700 ddr again as the lowest but 3200 ddr if your board can take it.
Then see what that feels like for gaming. Or just forgo current pleasures and save, save, save...

---

### Post by tintix on 2007-02-28
OK, a new graphic card. May be. Because my model (Inno 3d) has only a 64-bit memory bus. :( That means that the GPU can't access the data in the memory so fast how it needs. Am I right?

But any ideas with CPU?. When I'm using Compiz on Nvidia drivers (no XGL/AIGLX),  so my CPU-meter shows whole 100% usage, and the effects are lagging quite. What should it mean? So I'm sure it's the CPU (man, the Celeron D is the cheapest and the worst CPU ever made by Intel :( )

I just forgot, when I log-in in the recovery mode (as root) - Compiz has any lags. Can't understand... :confused:

---

### Post by dannyboy79 on 2007-02-28
well if you do go for a new cpu, your mb can only handle the 840 or the 920 per this: [http://www.biostar.com.tw/support/cpu/socket_775.php3#p4m800-m7a(v7.0](http://www.biostar.com.tw/support/cpu/socket_775.php3#p4m800-m7a(v7.0))
so you can't go with the core 2 duo unfortunately. i have read that by q2, the E4300 will be down to $133 and when overclocked using the stock hsf to 3.375GHz (375MHz x 9.0) at 1.468V can take the Core 2 Extreme X6800 and beat it by a 3.3% margin so don't waste your money on the E6300 or the E6400, go with the E4300 and overclock!

here are my references: [http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=2903&p=2](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=2903&p=2)

---

### Post by tintix on 2007-02-28
I knew that I can forgot the Core 2 CPUs. And I can't upgrade to DDR2 because of my motherboard. But I need a CPU which my DDR 400 RAM can handle. If I put a Pentium D 920, so won't my DDR slow it down so that the CPU won't use it's all resources? I need a CPU which isn't too fast for my motherboard. Don't wanna throw out spare money... Can I find somewhere on the internet a calculator to figure out the optimal CPU form my motherboard? Or should I forget all these worries and put the Pentium D 920? :confused:

---

### Post by dannyboy79 on 2007-02-28
the processor will always use all it's power, it's the ram that wont possibly. it's usually whether you want to run the ram at 1:1 or 5:4 or 3:4 or what. the processor fsb is probably 800 so your ram will be able to run 1:1 so you';ll be alright. here's the 920 for $129.99.
[http://www.pricegrabber.com/p__Intel_Pentium_D_920_Dual_Core_Processor,__15806380/](http://www.pricegrabber.com/p__Intel_Pentium_D_920_Dual_Core_Processor,__15806380/)

---

### Post by tintix on 2007-03-02
OK. Have found a D 915 - much cheaper, but it has 2.8GHz and 4MB L2 chache - gonna be faster than mu Celeron 2.53GHz. But how much?
But I can't understand the sense of DDR2. Because > **dannyboy79 said:**
> the processor will always use all it's power, it's the ram that wont possibly. it's usually whether you want to run the ram at 1:1 or 5:4 or 3:4 or what. the processor fsb is probably 800 so your ram will be able to run 1:1 so you';ll be alright.
  If my PC would have it (I'm afraid it supports only DDR1 @ 400MHz) so would it be faster? Or the same?
Also have heard that some motherboards have to be flashed (the BIOS has to be flashed) to support dual core. In the my one's manual is being told that it supports dual core's. And in the manufacturer web site is being sowed that my MB can handle up to Pentium D 840 or 920. [http://www.biostar.com.tw/support/cpu/socket_775.php3#p4m800-m7a(v7.0]("http://www.biostar.com.tw/support/cpu/socket_775.php3#p4m800-m7a(v7.0") But is it after flashing the bios or from stock? Because at the BIOS upgrades there are Pentioum 805 support. Or is only this particular CPU, which needs additional support of my BIOS?

---

### Post by dannyboy79 on 2007-03-02
no, your motherboard supports the chips I listed by default. If a motherboard has a bios upgrade, it's possible that it would support more cpu's but since the 840 and 920 were listed on the website, that would mean they are supported with the default bios (i would think?). Unless of course on the website it specifically states the bios name and you don't have that bios flashed yet? It's not hard to flash a bios though, you can do it with a  floppy disc or cd-rom, you just boot to it, then type in a few words, which flashs the bios chip with the new bios. most times it give you a chance to backup your old one in case the new flash doesn't work. I will warn you, you always want to make sure you don't flash a bios when you think the power may go out. so make sure your computer is hooked to a solid plug in the wall, not 1 that is hooked to a hair dryer, several lights, your printer etc etc. If the flashing is interupted while flashing, there's a very high possibility that it's junk now and you won't be able to flash it again. I just looked at the website for downloading a bios, according to this link, [http://www.biostar.com.tw/support/bios/socket.php3?socket=775](http://www.biostar.com.tw/support/bios/socket.php3?socket=775)
there are 3 different bios's for the VIA P4M800/VT8237 Chipset but I believe since you stated that you have the P4M800-M7A, then you just need to figure out if you have the 1.X or the 7.X. BUt I would say again, that based on what the website had at that link for cpu's, that by default your motherboard at least supports the ones listed. for dual core, the 840 or 920. I am not sure about the 915? You could always call biostar to make sure.

The Pentuim with 4mb L2 cache will be way faster than a Celeron, Celeron's normally only have like 512K of L2 cache. plus you are gaining in processor speed as well.

I am actually getting a new ASRock 775dual-VSTA and that supports both DDR and DDR2 and Anandtech did some benchmarking and found that on this motherboard the DDR2 didn't outperform the DDR by that much. So on this motherboard it doesn't matter. AS far as a general rule for DDR2 over DDR the main advantages are:
Speed - Data rate ranges 400 Mbps ~ 667 Mbps
Power - Lower than DDR SDRAM due to reduced I/O voltage and core voltage
Size - FBGA packages provide smaller footprints

you can read about it here:
[http://www.altera.com/technology/memory/dram/mem-dram.html](http://www.altera.com/technology/memory/dram/mem-dram.html)

---

