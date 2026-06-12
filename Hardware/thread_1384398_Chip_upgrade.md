---
title: "Chip upgrade?"
date: 2010-01-18
forum: Hardware
---

### Post by PartsMan on 2010-01-18
I now this is the Ubuntu forums. 
I also know that usually a processor upgrade isn't worth the trouble.

Here is my situation.

My Dell 2400 with P4 2.2 fried it's integrated graphics card and ethernet makeing it unable to run Ubuntu.
My step dad offered me a 2350 with a celeron 2.0.

Same chip set, same bus speed. Heck almost the same chip.

How do I change one for the other without ruining both?

---

### Post by pi/roman on 2010-01-18
[http://support.dell.com/support/edocs/systems/dim2350/index.htm](http://support.dell.com/support/edocs/systems/dim2350/index.htm)
[http://support.dell.com/support/edocs/SYSTEMS/dim2400/en/sm_en/index.htm](http://support.dell.com/support/edocs/SYSTEMS/dim2400/en/sm_en/index.htm)

The parts changing section provides instructions on both models.

Checking specifications, it looks as though the 2350 supports P4 2.0 and 2.4 but 2.2 is not listed so maybe you should request help from Dell with that.

---

### Post by blackened on 2010-01-18
Judging by their clock ratings, those all look like Northwood family processors and should be interchangeable. I have no explanation as to why they wouldn't include the 2.2ghz chip in the suggested replacements list.

---

### Post by PartsMan on 2010-01-18
I am a little worried about this one. I am not crazy for doing it am I?
I have changed everything in a PC before but the processor.

Any tips on removing and replacing the thermal paste?

---

### Post by blackened on 2010-01-18
Don't sweat it too much. The hardest part(s) will be removing/reinstalling the heatsink and fan. Be careful if you use a screwdriver on this part as one slip could potentially destroy your board. That said, I've never been able to install/remove one without using a screwdriver.

Pretty decent guide that'll save me some typing here -> [http://www.pcmech.com/byopc/step-5-install-the-cpu/]("http://www.pcmech.com/byopc/step-5-install-the-cpu/").

Don't over do it with the thermal paste. Use just enough to fill any airgaps left between the CPU and HSF. Good luck.

---

### Post by PartsMan on 2010-01-19
I also have a P4 2.53 laying on my bench.
I am right in thinking that the higher buss speed would not run?

---

### Post by cascade9 on 2010-01-19
2.0Ghz celeron to 2.2Ghz P4 is worth it. The P4s have double the cache, and that helps a lot. 10% increase in clock speed isnt to be sneezed at either. 

> **blackened said:**
> Judging by their clock ratings, those all look like Northwood family processors and should be interchangeable. I have no explanation as to why they wouldn't include the 2.2ghz chip in the suggested replacements list.

I'm thinking that is a  typo or something. the 2350s came out with 2.2s. 

> **PartsMan said:**
> I also have a P4 2.53 laying on my bench.
I am right in thinking that the higher buss speed would not run?

It wont in the 2350, it should in the 2400- 

> Intel® Pentium® 4 that runs at 2.2 or 2.4 GHz internally and 400 MHz    externally, or 2.266, 2.4, 2.53, 2.66, 2.8, or 3.06 GHz internally and 533 MHz    externally.

[http://support.dell.com/support/edocs/SYSTEMS/dim2400/en/sm_en/specs.htm](http://support.dell.com/support/edocs/SYSTEMS/dim2400/en/sm_en/specs.htm)

The 2.53 (533FSB) are much quicker than a 2.2 (400FSB). 

BTW, you might be able to get a cheap PCI video card, and PCI network card to make the 2400 run again.

---

### Post by PartsMan on 2010-01-19
> **cascade9 said:**
> 
BTW, you might be able to get a cheap PCI video card, and PCI network card to make the 2400 run again.

That has crossed my mind.
I have a PCI video card on it's way and use wireless internet anyway.

I'm just not sure I trust that board anymore. I has gremlins in it already.

---

### Post by cascade9 on 2010-01-20
Dont worry about gremlins. 

I've had a few 845 chipsets boards lose video, network, and other stuff (USB in particular) and keep going. Early 845 chipset boards havent got the best onboard video, or network, virtually anything you can put in there will run better.

Besides, your going to have a computer with no CPU once your swapped the current CPU out, and a CPU that will fit in there. Might as well use it.

---

### Post by PartsMan on 2010-01-20
Cascade9 you have some good points. I may just leave the 2350 stock(stable for school) and play with the 2400 to scratch the itch to tinker.

I really wish that I had a board I could overclock these things. I could afford to burn a couple. Word is that lowly Celeron will out run the other two with some tweaking.:)

---

### Post by cascade9 on 2010-01-20
I'd probably still try the 2.2Ghz P4 in the 2350. But if you dont have any other computers to use then it might not be worth the risk.....

> **PartsMan said:**
> I really wish that I had a board I could overclock these things. I could afford to burn a couple. Word is that lowly Celeron will out run the other two with some tweaking.:)

Overclocked to all hell, then yeah, the celeron might pull ahead on some tasks. The main issues with the (early) P4 celerons is lack of cache (128K is just not enough) and low FSB. The cache problem isnt beatable, but you can overclock the celerons quite a bit.....probably up to 2.6Ghz (for 533 FSB) without 'exotic' cooling solutions, like cooling or phase change. At 2.6Ghz, the celeron would probably do over a 2/2.2Ghz P4......the 2.53 P4 would be much faster though.

---

