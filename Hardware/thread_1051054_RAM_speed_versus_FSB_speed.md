---
title: "RAM speed versus FSB speed"
date: 2009-01-26
forum: Hardware
---

### Post by gobbles414 on 2009-01-26
Hi all,

Sorry for my ignorance, but I am trying to find an easy way to know what speed RAM a front side bus can support. For example, can a 1066 MHz FSB run 1066 MHz RAM at full speed, or is 800 MHz RAM the maximum? Does the answer change depending on whether the RAM is DDR2 or DDR3? Thanks!

PS: I'm sorry if this question has already been asked; I searched but couldn't find any similar posts.

---

### Post by electrogeist on 2009-01-27
**FSB: **The 1066 MHz Front Side Bus (FSB) of the processor, well Intel advertises it in "quad pumped" figures.  In reality the true FSB is 1/4 that = 266 MHz FSB
[LIST]
[*][http://en.wikipedia.org/wiki/Quad_Data_Rate](http://en.wikipedia.org/wiki/Quad_Data_Rate)
[*]	[http://en.wikipedia.org/wiki/Pumping_(computer_systems)](http://en.wikipedia.org/wiki/Pumping_(computer_systems))  <-- (currently has poor DDR2 example that uses 1:2 ratio not 1:1)
[/LIST] 

**DDR** uses double pumping to essentially double the speed.  If a P4 processor had a 800 MHz quad pumped FSB, the true FSB being 1/4 that is 200 MHz.  For a 1:1 FSB to memory ratio, it would be matched up in the table below to the 200 MHz memory bus clock of DDR-400 / PC-3200
[LIST]
[*][http://en.wikipedia.org/wiki/DDR_SDRAM](http://en.wikipedia.org/wiki/DDR_SDRAM)
[/LIST]

**DDR2** also uses double pumping, in addition to doubling the bus clock.  This does add some latency (lag) but the benefit of extra bandwidth.  A P4 or Core2 processor with a 1066 MHz quad pumped FSB has a true FSB of 266 MHz.  For a 1:1 FSB to memory ratio, it would be matched up to the 266 MHz  memory bus clock of DDR2-533 / PC2-5300
[LIST]
[*][http://en.wikipedia.org/wiki/DDR2_SDRAM](http://en.wikipedia.org/wiki/DDR2_SDRAM)
[/LIST]

**DDR3** also uses double pumping, and 4x the bus clock.  This adds even more latency but of course the benefit of even more bandwidth.  I believe for DDR3 most people are using 1:2 FSB to memory ratios, where the memory is running twice the speed of the FSB, and I guess that helps make up for the poor latency.  A P4 or Core2 processor with a 1066 quad pumped FSB has a true FSB of 266 MHz.  With a 1:2 FSB to memory ratio, it would be matched up to the 533 MHz  memory bus clock of DDR3-1066 / PC3-8500.  
[LIST]
[*][http://en.wikipedia.org/wiki/DDR3_SDRAM](http://en.wikipedia.org/wiki/DDR3_SDRAM)
[/LIST]


**This little chart I made should be handy:**
```
DDR memory						CPU commonly used with:

			Memory		Memory		CPU FSB	   @	cpu:mem
Name			Clock		Bus Clock	true (quad)	ratio
~~~~~~~~~~~~~~~~~~~~	~~~~~~~~~~~~	~~~~~~~~~~~~~	~~~~~~~~~~~~~~~~~~~~~~~
DDR-200	/ PC-1600	100 MHz		100 MHz		100 (400)  @ 1:1 ratio
DDR-266	/ PC-2100	133		133		133 (533)  @ 1:1 ratio
DDR-333	/ PC-2700	166		166		166 (666)  @ 1:1 ratio
DDR-400	/ PC-3200	200		200		200 (800)  @ 1:1 ratio

DDR2-400  / PC2-3200	100 MHz		200 MHz		200 (800)  @ 1:1 ratio
DDR2-533  / PC2-4200	133 		266		266 (1066) @ 1:1 ratio
DDR2-667  / PC2-5300	166		333		333 (1333) @ 1:1 ratio
DDR2-800  / PC2-6400	200		400		400 (1600) @ 1:1 ratio
DDR2-1066 / PC2-8500	266		533		533 (2133) @ 1:1 ratio

DDR3-800  / PC3-6400	100 MHz		400 MHz		200 (800)  @ 1:2 ratio
DDR3-1066 / PC3-8500	133		533		266 (1066) @ 1:2 ratio
DDR3-1333 / PC3-10600	166		667		333 (1333) @ 1:2 ratio
DDR3-1600 / PC3-12800	200		800		400 (1600) @ 1:2 ratio 
```

**Ratios:**  Some DDR/DDR2 motherboards will also allow for ratios other than 1:1 synchronous operation.  Usually if running asyncronously, you would want the memory to run faster than the FSB.  Such as a 4:5 ratio of a 1066 quad FSB CPU with PC2-5300 memory, however real world performance may not always benefit.  Lower ratios may also be forced, for example it is not uncommon for boards supporting Nocona Xeons with 800 quad FSB to only support PC-2700R, which is pathetic to have reduced bandwidth considering there are usually 2 cpus in that situation.  As previously noted, with DDR3 most people are using 1:2 FSB to memory ratios.

**Interchangability**: Note that DDR, DDR2, and DDR3 are *not* interchangable.  They use different voltages, pinouts, and are keyed differently.  There are some oddball motherboards which may have 2 banks for 2 different types (or older PC133 SDRAM and DDR)...those would most likely use either one bank or the other, not two different kinds of memory at once.  And as previously noted, with DDR3 most people are using 1:2 FSB to memory ratios.

**Overclockers memory**:  Some may only be operational with a higher voltage and possibly not have the normal speeds programmed in the SPD on the module.  This has been known to cause issues for motherboards that lack the ability to provide a voltage higher than industry standards, or for inexperienced people.  Just regular, quality name-brand memory should be fine.

**Pairs**: Always use matched pairs, as every decent motherboard should be able to support dual channel!

**More info**: This presentation from Corsair is a little bit dated but is excellent at conveying the information it covers, which is alot more than most people ever wanted to know about memory:
[LIST]
[*][http://www.corsair.com/memory_basics/index.html](http://www.corsair.com/memory_basics/index.html)
[/LIST]



So for DDR2 you only need PC2-4200 for a 1:1 ratio - but you might find PC2-5300 or PC2-6400 to be same price or even cheaper and it should work just fine at slower speeds, and be more useful in the future.  For DDR3, PC3-8500 will run at a 1:2 ratio.

Yes I am assuming Intel, because AMD doesn't have a Front Side Bus. AMD has the hypertransport speed and memory is selected based off that...

---

### Post by gobbles414 on 2009-01-28
Thanks for your reply electrogeist! Yes, my questions is about Intel processors. Specifically, I'm trying to decide whether I should buy one of Apple's newly refreshed white MacBooks, or one of the new aluminum MacBooks. Either way, I would replace the Apple's 5400 RPM drive with a 7200 RPM drive and then triple-boot Ubuntu, OS X, and Windows Vista. My remaining questions are:

* It's difficult for me to believe that 533 MHz DDR2 RAM performs as fast as 800/1066 MHz DDR2 RAM. Electrogeist, did I misunderstand your answer?

* How is DDR3 different from DDR2? Both the aluminum MacBooks and new white MacBook use a 1066 MHz FSB, but Apple is using 1066 MHz DDR3 RAM in the aluminum MacBooks. Does this mean that "quad pumping" doesn't apply to DDR3 systems?

* If it's even possible to do so, would replacing Apple's 667 MHz DDR2 RAM with 800/1066 MHz DDR2 RAM in the new white MacBook result in a noticeable increase in performance?

* How much faster are the aluminum MacBooks than a new white MacBook? I want a laptop with a FireWire port, but would be willing to sacrifice the FireWire port if it means a truly significant increase in speed.

* I want to make sure that I understand what dual-channel is all about. Two sticks of identically-sized RAM will run in dual-channel mode, which means that 667 MHz memory in that configuration actually runs at an overall speed of 1334 MHz. Obviously, that's overkill for a 1066 MHz front side bus. So to make 800/1066 MHz DDR2 RAM worthwhile, the MacBook would need at least a 1600 MHz front side bus. Am I correct so far? Does dual-channel work the same regardless of whether it's DDR2 or DDR3?

* What are some general guidelines for matching RAM speed to AMD's HyperTransport? Does the same rules work with Intel's QuickPath technology?

Thanks for taking the time to answer so many questions!

---

### Post by electrogeist on 2009-01-28
Ok I totally overhauled my original reply above.  I was not happy with my original answer either on this complex and confusing topic.  And I will probably refer people to this post in the future and/or reuse that.

---

### Post by cariboo on 2009-01-28
You are paying way to much attention ot marketing blurbs and not enough to technical details. Find the model number of the motherborad of the computer you are looking at, then go to Intel's web site and do a search for that motherboard. Intel provides way more technical data than most home users need.

Jim

---

### Post by electrogeist on 2009-01-28
> **gobbles414 said:**
> Thanks for your reply electrogeist! Yes, my questions is about Intel processors. Specifically, I'm trying to decide whether I should buy one of Apple's newly refreshed white MacBooks, or one of the new aluminum MacBooks. Either way, I would replace the Apple's 5400 RPM drive with a 7200 RPM drive and then triple-boot Ubuntu, OS X, and Windows Vista. My remaining questions are:

* It's difficult for me to believe that 533 MHz DDR2 RAM performs as fast as 800/1066 MHz DDR2 RAM. Electrogeist, did I misunderstand your answer? 
No it doesn't perform the same, unless they are running at the same speed. And yes, it was misunderstood... but it is confusing.  _Hopefully my revised reply above sheds some light on it_

> 
* How is DDR3 different from DDR2? Both the aluminum MacBooks and new white MacBook use a 1066 MHz FSB, but Apple is using 1066 MHz DDR3 RAM in the aluminum MacBooks. Does this mean that "quad pumping" doesn't apply to DDR3 systems?
My revised reply above should answer the first part.  

As far as the Macbooks:  The white one uses DDR2-667 per their site, and if that CPU has a 1066 FSB it would be either running asyncronously at a 4:5 fsb:mem ratio, or syncronously 1:1 with the memory not running at full speed.  The latter (1:1) wouldn't surprise me...then when they have 1333 FSB CPUs in there later they can say DDR2-667 is the correct ram for the whole line.  IIRC they did that with the very first iMac G5 too, which had a slightly lower FSB than the rest.  The aluminum one with DDR3-1066 would be running at the 1:2 fsb:mem ratio that is common.

Until now I didn't realize they dropped from DDR3 to DDR2.  I've heard  the latency is pretty bad with DDR3 and not much benefit with current hardware.

> * If it's even possible to do so, would replacing Apple's 667 MHz DDR2 RAM with 800/1066 MHz DDR2 RAM in the new white MacBook result in a noticeable increase in performance?
Probably not...being an Apple I don't think that you can change the ratio.  Apples have never had a BIOS setup, and if they did it would not be flexible.  Well I take that back, OpenFirmware on the old PPC models was flexible, just cryptic as hell.  The Intel Macs now use EFI...maybe it is possible with some hacking, but I don't know much about it.

> * How much faster are the aluminum MacBooks than a new white MacBook? I want a laptop with a FireWire port, but would be willing to sacrifice the FireWire port if it means a truly significant increase in speed.
Well according to their site the older aluminum model has the option of a 2.4 GHz c2d, while the new white one only has a 2.0 for now.  IIRC the older ones might be easier to work on.  The white one is cheaper.  You probably want to dig around some apple forums or lowendmac to learn the nitty-gritty differences

> 
* I want to make sure that I understand what dual-channel is all about. Two sticks of identically-sized RAM will run in dual-channel mode, which means that 667 MHz memory in that configuration actually runs at an overall speed of 1334 MHz. Obviously, that's overkill for a 1066 MHz front side bus. So to make 800/1066 MHz DDR2 RAM worthwhile, the MacBook would need at least a 1600 MHz front side bus. Am I correct so far? Does dual-channel work the same regardless of whether it's DDR2 or DDR3?
In the real world, dual channel is not twice the speed.  But definately worth utilizing when the hardware supports it.  Quality motherboards from DDR(1) onwards support dual channel.  I even have a Pentium 3 with dual channel PC133! 

> * What are some general guidelines for matching RAM speed to AMD's HyperTransport? Does the same rules work with Intel's QuickPath technology?
I may not be the best person to answer this.  But I think the 2 technologies are similar.  And you don't have to divide those speeds by 4.

> Thanks for taking the time to answer so many questions!
Thats ok I am sitting here on unemployment :)

---

### Post by Cracauer on 2009-01-29
Trust is that outside of artificial memory bandwidth tests applications don't really care about memory and FSB speed that much. 2-3% net for major speed changes.

---

