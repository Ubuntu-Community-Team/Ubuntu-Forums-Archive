---
title: "Computer won't boot, possible hardware failure; help."
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by llano on 2007-07-01
Hello all,

My worst fear has finally been realized, I have a dead computer on my hands with no idea what is wrong, or how to begin to fix it. I write this from a roommates computer. I'll build up the scenario here; the other day I was doing normal tasks, web browsing, listening to music, running uTorrent, talking on Pidgin, etc., when my computer experienced a random lock up. Screen completely froze, no mouse or keyboard response. I powered it down, let it rest a bit, and then turned it back on. Motherboard started giving me the beep error, but I don't know what the cause is.

The CPU fan was dirty so I cleaned it. I realized my rear case fan and stopped working (going to replace it), did general cleaning throughout the case to see if there was anything dirty, loose, etc. I ended up completely deassembling the computer and rebuilding to see if that would help, still no luck. Everything powers up, but the motherboard keeps giving me the error beep. I get no post, no bios, nothing. Just a motherboard beep error. This makes me think there is a problem with my CPU. I guess it is important to note that when I cl eaned the CPU fan the CPU was literally stuck to the bottom of the heatsink (maybe it overheated and is now dead), I had to pop off the CPU by prying on it in order to reassemble the mobo, cpu, heatsink.

So, how do I go about testing this? Is there a way to eliminate problem areas (such as video card, ram, hard drives, CPU) on a case by case test? Does it sound like the CPU overheated, due to the fact that it was stuck to the heatsink?

Any ideas on how to begin to diagnosis this situation is appreciated. I don't want to buy parts if it isn't going to fix the problem.

Thanks,
Llano.

Edit: Computer Parts / Specs

Mobo:  	 AOpen AK89 MAX Socket 754 NVIDIA nForce3 150 ATX AMD Motherboard
CPU: AMD Athlon 64 3400+ ClawHammer 2.2GHz Socket 754 Processor Model ADA3400BOX
Ram:  	 mushkin 512MB 184-Pin DDR SDRAM DDR 400 (PC 3200) Desktop Memory Model 991093 (x2)
Video Card: Connect 3D Radeon X800 XT / 256MB GDDR3 / AGP 4x/8x
Harddrive: Maxtor DiamondMax Plus 9 6Y120M0 120GB 7200 RPM Serial ATA150 Hard Drive
DVD:  	 NEC DVD Burner Black IDE Model ND-2510A
OS: Ubuntu 7.04
Age: Built August 2004

Only previous problem was a dead PSU that I replaced about a year ago.

---

### Post by logos34 on 2007-07-01
> **llano said:**
> Hello all,

My worst fear has finally been realized, I have a dead computer on my hands with no idea what is wrong, or how to begin to fix it. I write this from a roommates computer. I'll build up the scenario here; the other day I was doing normal tasks, web browsing, listening to music, running uTorrent, talking on Pidgin, etc., when my computer experienced a **random lock up**. Screen completely froze, no mouse or keyboard response. I powered it down, let it rest a bit, and then turned it back on. Motherboard started giving me the **beep error**, but I don't know what the cause is.

The CPU fan was dirty so I cleaned it. I realized my rear case fan and stopped working (going to replace it), did general cleaning throughout the case to see if there was anything dirty, loose, etc. I ended up completely deassembling the computer and rebuilding to see if that would help, still no luck. Everything powers up, but the **motherboard keeps giving me the error beep. I get no post, no bios, nothing. Just a motherboard beep erro**r. This makes me think there is a problem with my CPU. I guess it is important to note that when I cl eaned the CPU fan t**he CPU was literally stuck to the bottom of the heatsink (maybe it overheated and is now dead), I had to pop off the CPU by prying on it in order to reassemble the mobo, cpu, heatsink.**


All I can say is: ouch.  

You needed to check your motherboard manual first for those beep codes--the pattern indicates where the problem lies.  It could be something as simple as a RAM stick becoming unseated.  Your problem is also consistent with a second power supply failure.  (Maybe it's a cheap replacement unit, it's underpowered, or you were just born unlucky).  Other possible reasons: overheating/insufficient case cooling (i.e.rear fan).  Maybe the southbridge needs a small passive heatsink/fan.

You may have done more harm than good.  Sounds like your heatsink used a cheap thermal patch--they stick like welded steel, making separating the HSF and cpu a nightmare.  (The silicon paste is so much better).  But there's a lever you have to raise before you take the processor out of its seating.  Wouldn't be surprised if you lost a pin or two.

---

### Post by llano on 2007-07-02
> **logos34 said:**
> All I can say is: ouch.  

You needed to **check your motherboard manual first for those beep codes--the pattern indicates where the problem lies**.  It could be something as simple as a RAM stick becoming unseated.  Your problem is also consistent with a second power supply failure.  (Maybe it's a cheap replacement unit, it's underpowered, or you were just born unlucky).  Other possible reasons: **overheating/insufficient case cooling** (i.e.rear fan).  Maybe the southbridge needs a small passive heatsink/fan.

You may have done more harm than good.  **Sounds like your heatsink used a cheap thermal patch--they stick like welded steel, making separating the HSF and cpu a nightmare**.  (The silicon paste is so much better).  But there's a lever you have to raise before you take the processor out of its seating.  **Wouldn't be surprised if you lost a pin or two**.

I really wish I could figure out the error codes; my motherboard comes with "Dr. Voice II" which is supposed to make it easy to possible problems.
> Dr. Voice II is the second version of Dr. Voice. Dr. Voice II can identify what kind of problems have occurred in the operating system. It can even clearly “tell” whether there is a component issue or an installed issue, such as CPU, memory module, VGA, PCI add-on card, FDD, HDD or keyboard by voice
But that is a bunch of BS. I can only get the Dr. Voice feature to output through the buzzer, which tells me nothing, changing the jumper to speaker mode doesn't work for some reason.

As for the heatsink...it was a cheap thermal patch; makes me think that the CPU overheated. All the pins were OK on the CPU however, so that least that isn't the problem.

I'm still stuck on this one, any other ways to determine what part of the hardware has failed?

Thanks,
Llano.

---

### Post by IntuitiveNipple on 2007-07-02
From page 76 of the manual:
> Currently there are two kinds of beep sound when system fails to boot at POST. The first type of beep sound consists of a single long beep and two short beeps, indicating a video error has failed BIOS from initializing video screen for displaying any additional information. The 2nd type of beep sound is a single long beep that beeping repeatedly, signaling a DRAM error has
occurred. You may look over the indicated error according to different beep significances.

[Manual downloads page](http://asia.aopen.com.tw/userdownload_List.aspx?RecNo=7368&Model=AK89%20Max)

---

### Post by logos34 on 2007-07-02
It's all a matter of a process of elimination and deduction.  Disconnect everything from the board--hard drives, cdrom, add-in cards.  Just focus first getting rid of the error beep.  

I'd focus on memory first.  Try reinstalling the RAM stick(s).  Try different dimm slots.  It can be tricky to get them seated just right so they are recognized by the motherboard.  (Be careful not to touch the gold-plated connectors/teeth).   The other two likely causes are a failing PSU or fried CPU.  It may seem like it powers up ok, but it could still be a failing psu--the only way to know is to swap it with a known good one.  If it's not that, then it's either the CPU or motherboard itself.  Do you at least have this computer connected to a power-surge strip? (APC is a better idea).  Could have been a power surge that caused the problem, in which case I'm not sure what all damage it could have done.  

Usually when a power supply is going bad on you it gives you some signs if not explicit error messages  like +12V and +5V under- and overvoltages (I don't know what kind of hardware monitoring you have on this thing).  If the processor overheated it would normally shut down automatically after a certain temp threshold.

---

### Post by llano on 2007-07-02
Thanks for the help guys, I appreciate the advice.

I'll try and convince my roommate to let me cannibalize his 2nd computer for testing purposes. I won't be able to do try this until I get home from work so I'll post my results later tonight/tomorrow.

---

### Post by llano on 2007-07-02
We have a winner! Dead video card; thats what I get for buying a third-party manufacturer of a video card. Next step: Finding a replacement AGP card for basic 3D (need to play WoW). I also ran into a SATA link down on my ubuntu boot. Time to start searching the forums for this one.

Thanks for the help logos34! I was about to go buy a CPU when it was my videocard.

---

