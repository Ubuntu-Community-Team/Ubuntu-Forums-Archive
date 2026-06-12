---
title: "Ubuntu killed my motherboard?"
date: 2014-07-28
forum: Hardware
---

### Post by fatriff on 2014-07-28
Okay, so I have a 3 week old install of 14.04 installed on my machine which has a ASRock Extreme Pro 3.. 

I always had the issues with resuming when the computer went to sleep with Ubuntu in that the machine would refuse to wake.. The machine was clearly running (all fans spinning, components warm) but nothing on the display and no response from keyboard etc and I would end up killing the power.. This is just something I accept happens every once in a while on Ubuntu..

The same thing happened yesterday, Got up, went to resume and machine unresponsive, held in the power button and went to power on again and it hasn't worked since. If I dissconnect from the mains then plug back in the machine comes on (power light, fans spinning etc), but nothing at all, no display.. No signal message is displayed on monitor...

I investigated what could possibly be wrong, I remove hard drives, ram, tried another graphics card from another machine and still the same, the machine was clearly running but it's not even going past the initial bios checks as there is no beeps.. I would normally hear one beep as the bios splash screen transitions into boot mode... 

Lastly after checking everything I could think of I get to the CPU.. now how could that be damaged?? I remove it and turn machine on.. The exact same behaviour as when it's seated in the board (fans spinning, power light on etc)... So it can't be the CPU... Now what??? 

So I decide the test the cpu in another machine and the machine boots perfectly.. So it's defo not the CPU.. 

Something on the mobo has failed, perhaps the cpu socket? as the cpu is stone cold when the machine is running (I can even remove the heatsink and feel the cpu and it is stone cold while the machine is on!), all the other components warm up as they should, just nothing happens, the machine just runs and no output whatsoever.

So how could the CPU socket on a 7 month old board fail? (If that's what it is)... I haven't touched the case or the CPU since the day I got the mobo and this was the 1st time i'd opened the case even.

Having removed the mobo from the machine i've now put another board in and same ram, cpu, hard drives, and gpu as before and I have a perfectly working machine again.

Do motherboards really just fail for no reason?? If they do it's the 1st time it's ever happened to me in my 20 years of intense computing and on a 7 month old board??

Any ideas people as this whole experience has annoyed me somewhat.. 

When I had rebuilt the machine using another board, on 1st boot into Ubuntu there was the expected Ubuntu encountered an error and it mentions resume in that error..

---

### Post by jeremy31 on 2014-07-28
Check the power supply

---

### Post by fatriff on 2014-07-28
Defo not the power supply, tested with another psu from a fully working machine.. Plus the repaired machine with another mobo I had is working perfectly with the same power supply as the mobo which is now broken was using. Everything is exactly the same now apart from i've changed the mobo and everything is working perfectly now.

Sorry, completely slipped my mind to mention the psu in everything I said above..

---

### Post by jeremy31 on 2014-07-28
Strange things happen, I had what looked to be an insect short a motherboard years ago

---

### Post by tgalati4 on 2014-07-28
Where the term "bugs" come from.  Yes, motherboards do fail, but it could be a manufacturing issue.  Removing lead and gold from motherboard manufacturing means the boards are less reliable than from years ago.  Do a search on your specific board and see if others are having the same problem.  If so, then you may have found your problem.

---

### Post by jeremy31 on 2014-07-28
> **tgalati4 said:**
> Where the term "bugs" come from.  Yes, motherboards do fail, but it could be a manufacturing issue.  Removing lead and gold from motherboard manufacturing means the boards are less reliable than from years ago.  Do a search on your specific board and see if others are having the same problem.  If so, then you may have found your problem.

It was about 7 years ago when there were a lot of issues with some capacitors on motherboards failing.  We had 8 of them where I work

---

### Post by ian-weisser on 2014-07-28
> **fatriff said:**
> I always had the issues with resuming when the computer went to sleep with Ubuntu in that the machine would refuse to wake.. 

Not all motherboards properly support Suspend and/or Hibernate. Most do.
Apparently yours seems to be,well, not one of them.

Could be due to a design fault, a manufacturing fault, a proprietary design, or a BIOS bug. None of those are Ubuntu's fault. If developers had access to the hardware or proper documentation, and it worked properly as documented, then Ubuntu would support it.



> **fatriff said:**
>  I investigated what could possibly be wrong, I remove hard drives, ram, tried another graphics card from another machine and still the same, the machine was clearly running but it's not even going past the initial bios checks as there is no beeps.. I would normally hear one beep as the bios splash screen transitions into boot mode...

If your motherboard is powering on, but not passing the Power On Self Test (POST), then you clearly have a hardware fault somewhere on the motherboard. Time to replace it. Identifying a hardware fault that prevents the BIOS and OS from loading is precisely what the POST is for.

Any more detailed information needs to come from the motherboard manufacturer; without additional POST information from them you lack the information you need to troubleshoot further. The BIOS and motherboard will not function unless the POST is successful. Beyond knowing that the motherboard has gone, it's rather a waste of time to search further.

I don't see how a motherboard gone bad (it's rare, but they do) has anything to do with Ubuntu. Check your purchase record for the motherboard - they often come with a warranty against precisely this circumstance.

I have had two motherboard fail on me in the past 10 years - it's rare, but power surges, manufacuring defects, drops and falls, etc. do happen.

---

### Post by Yellow Pasque on 2014-07-29
Try resetting the CMOS?

---

### Post by M._Gruber on 2014-07-29
Doesn't the Extreme 3 mobo have a POST debug display like this?
[img]http://www.asrock.com/mb/sticker/DrDebug-desc.jpg[/img]
It should display something...

---

