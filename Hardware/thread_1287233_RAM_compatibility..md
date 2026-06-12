---
title: "RAM compatibility."
date: 2009-10-09
forum: Hardware
---

### Post by A Traveller on 2009-10-09
Hi All.

I just wanted to ask if anyone knew of any compatibility issues using Gskill memory with Linux (particularly Ubuntu).

Thanks.

---

### Post by jeremyswalker on 2009-10-09
Not a bit. That's virtually all I buy is Gskill RAM. I've never had an issue.

---

### Post by kathir678 on 2009-10-10
Best thing to do is just go to your manufacturer of your mother board on their website and see what is compatible and what works and doesn't to save you some time. But i have yet in 17 years Damage a MB putting in incompatible memory i either get beeps or it doesn't boot or does and i get BSOD's or it works and no problems.
____________________________________________________
[number plates](http://www.4plates.co.uk/builder.asp)  [laboratory automation](http://labface.com/Laboratory-Automation-7)

---

### Post by Anubis on 2009-10-10
:lolflag:

---

### Post by A Traveller on 2009-10-10
Thanks for all the replies.

I have already looked at the motherboards specs, which only state the following about Linux.

"Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website."

Which chipsets do they mean? Are they referring to the following:

North Bridge: AMD 785G
South Bridge: AMD SB710

I had also found gskill memory on their supported list of RAM, however, it was the Linux/Ubuntu compatibility I was worried about. They don't say anything about Linux in the memory section. I have read in another thread that some memory require tweaking setting. Does Gskill RAM need any tweaking?

It is reassuring that damaging components is rare, however, I am also worried about wasting my money on RAM that doesn't work.

Thanks.

---

### Post by HankB on 2009-10-10
> **A Traveller said:**
> 
I have already looked at the motherboards specs, which only state the following about Linux.

"Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website."

Which chipsets do they mean?...
They're probably talking about the processor chipset. I suspect their statement is more a disclaimer than a real concern. Unless you have a mobo with a pretty unusual chip set, it will most likely run right out of the box without any special effort on your part.

Best bet is to google for "<motherboard name> linux compatibility" or "<chipset name> linux compatibility" and see if anything comes up. You are probably not the first to try Linux on your mobo and if there any problems, you should get a clue about that in the search results.

RAM compatibility is not usually an issue with Linux, though years ago there were situations where systems had difficulty running Linux due to flaky RAM. The same systems probably had frequent BSODs running Windows but in those days Windows was so flaky it usually took the blame.

-hank

---

### Post by jeremyswalker on 2009-10-10
Like I said before, virtually the only memory I buy is Gskill. I haven't had a single problem with it. As far as Linux compatibility, that should not even be a concern (as the previous poster said). All of my systems run Linux with Gskill RAM.

---

### Post by pietjanjaap on 2009-10-10
chipset on motherboard is the chip that's connect/controls de cpu, memory, harddisk etc together(via chip is a example). It has nothing to do with ram memory.

Install memory in your motherboard, then start your pc with memtest86(bootable cd, boot from the cd), this starts automaticly and after 10 hours there should be 0 errors. Then it's good.
If not good then find the specs of your ram memory of the producer and check the settings in your pc. Maybe you need more voltages, or make the settings of the memory looser(see overclocking, but the other way around).

Better is to check the maker of the motherboard, there is a list of ram memory wich will work with this motherbord.

---

### Post by A Traveller on 2009-10-10
Ok, thanks everyone.

---

### Post by A Traveller on 2009-10-13
jeremyswalker, I forgot to ask; have you used G Skill memory with AMD CPUs/motherboards, or were all of yours Intel?

Mine will be a Gigabyte GA-MA785GT-UD3H AM3 Motherboard (AMD). Most of the G Skill memory have the following (or similar) in its specifications.

Main Board - Intel
M/B Chipset - Intel P55

No mention of AMD at all!

Thanks.

---

