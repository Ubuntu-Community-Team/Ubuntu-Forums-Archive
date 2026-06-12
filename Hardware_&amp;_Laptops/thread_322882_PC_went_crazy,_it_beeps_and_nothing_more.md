---
title: "PC went crazy, it beeps and nothing more"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by finferflu on 2006-12-21
Hi everybody,

It looks like this is my unlucky period. I've got a strange problem with my mother's PC, a Pentium 3, 600Mhz, 128 Mb RAM, Xubuntu Dapper install. 

Up to yesterday night it was working fine. Today she went to switch it on, and beeps, only long and periodic beeps, nothing more. It won't switch on and both the yellow and the green lights are solid. 

No idea of what it's happening, I can only think it's on the hardware side. Any hint?

Thanks a lot!

---

### Post by darrenm on 2006-12-21
Power cable out the back, side off and bridge the CMOS jumper or JBAT jumper.

Power cable back in and turn on.

---

### Post by finferflu on 2006-12-21
Thanks for your quick reply, but I don't quite understand what I am supposed to do, where should I find those components?

Thanks!

---

### Post by zgornel on 2006-12-21
It is probably a hardware failure : processor (unlikely), memory or graphics card. Open the pc, remove the ram, clean the dust and reinsert the modules. Same think for the graphics card. If you have the manual of the motherboard, search for these beeps or diagnostic leds (if you have such a thing) in the troubleshooting section. 
If you have other PC components that work with the current configuration, test them on the system and see if it behaves normally.
EDIT: previous post tells you to reset bios settings through jumpers on the mobo. They're near the battery usually :) He's saying to power off, pull the power cable out of the pc, reset bios, put the cable back in.

---

### Post by darrenm on 2006-12-21
> **finferflu said:**
> Thanks for your quick reply, but I don't quite understand what I am supposed to do, where should I find those components?

Thanks!

Near the CR2032 battery. There should be a jumper that you move from pins 1-2 to 2-3 for a few seconds to clear the CMOS then back.

---

### Post by finferflu on 2006-12-21
No joy! I first tried with the jumper, then I disconnected all I could possibly disconnect, and put it back, trying to remove any possible dust... still beeping...

---

### Post by darrenm on 2006-12-21
Next one then as above is to pull the VGA card out and put it back in. Older AGP cards are notorious for slipping out of place.

---

### Post by //RF on 2006-12-21
Try to take the battery off from motherboard for a few minutes, sometimes the clearing CMOS with jumper is not enough.

---

### Post by Sef on 2006-12-21
You need to know who manufacturers your BIOS.  Beeps can vary by manufacturer.   

[BIOS Beeps]("http://www.computerhope.com/beep.htm")

---

### Post by finferflu on 2006-12-21
I think you're right, in fact on my VGA card there was a security strip for that purpose, a piece of plastic to keep it in its proper place. I removed it anyway, removed the card, put it back, put the security back, and still nothing...

---

### Post by finferflu on 2006-12-21
> **//RF said:**
> Try to take the battery off from motherboard for a few minutes, sometimes the clearing CMOS with jumper is not enough.

I'm just doing that right now.

> **Sef said:**
> You need to know who manufacturer's your BIOS.  Beeps can vary by manufacturer.   

[BIOS Beeps]("http://www.computerhope.com/beep.htm")

How do I know my manufaturer's BIOS? I bought this PC on eBay, so I don't have any user's manual. Is there any other way to know that?

Thanks.

---

### Post by finferflu on 2006-12-21
Ok, the battery thingy didn't work..

---

### Post by //RF on 2006-12-21
If you have more than 1 memory modules, remove all the others and try with 1 module only.
If you have only one module, try to put the memory to other memoryslot(s).

---

### Post by finferflu on 2006-12-21
> **//RF said:**
> If you have more than 1 memory modules, remove all the others and try with 1 module only.
If you have only one module, try to put the memory to other memoryslot(s).

Yes! you got it! I removed one of them, and now the machine is on again. What was the problem? Defective memory stick?

Thanks a lot!

EDIT: I put the other stick back again, and now the machine works anyway... weird...

---

### Post by darrenm on 2006-12-21
Same thing as the VGA card thing. Over time the heat expands stuff then cooling contracts it over and over again which works things loose.

---

### Post by //RF on 2006-12-21
Good to hear that it's working, was going to tell you that the other stick is probably dead.... but now as it works with both of them, I'll stay quiet :)

---

### Post by finferflu on 2006-12-21
Well, I didn't mention that I had removed those sticks and put them in different slots, I've got 2 sticks and 4 slots, so I was playing around with them, and it didn't work. Then I did that trick of keeping only one, and it worked! Then I put the other stick back, and it worked anyway!

---

### Post by zgornel on 2006-12-21
Dust ...

---

### Post by finferflu on 2006-12-21
lol!

---

