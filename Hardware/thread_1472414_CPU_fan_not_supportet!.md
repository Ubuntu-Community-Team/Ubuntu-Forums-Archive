---
title: "CPU fan not supportet?!"
date: 2010-05-04
forum: Hardware
---

### Post by FreeRide23 on 2010-05-04
Hi, my name is Claus and i have the following problem:

I have installed Ubuntu on a Laptop and the CPU Cooler doesnt start "normaly"
The "sympthom" is following, when i start the PC, the fan is active until Ubuntu is beginning to load (when POST and BIOS stuff is completet) then the fan is turned off (couse the temp is under the critical point), but the problem is that the fan doesnt start when the CPU temp is getting higher (automatic cooling), so the temp gets higher and higher until the critial point is reached -> shut down. Then is start the PC again, and NOW the fan is RUNNING ALLTIME (couse its too hot), but now the fan doesnt STOP... so i think there is a communication problem between hard ware and soft ware.
To run it "normally" i have to "manualy crash down" the PC (overheating) and then restart it and then i can work...

I am a IT technichian, but only in windows, and i am very new in linux environment :D

Here are the technical details:
Ubunto 10.04 rc
Kernel 2.6.32-21-generic
Gnome 2.30.0
Acer Aspire 5315 Model ICL50 L07
Mainboard is the HannStar J MV-4

I have two CPU's, one from an other PC (customer, where his PC is broken, so i recicled the CPU) and the original

The one wich is build in now, is the one from the other PC
Intel Celeron Dual CPU T2410 @ 2.00Ghz
LF80537 T2410
7813B676 SLA4G
2.00/1M/533

and the original is the:
LF80537 550
7807A520 SLA2E
2.00/1M/533

So when you need any more information...

Thanks for your help!

---

### Post by bth73 on 2010-05-04
this is a problem with acer's there is some post on this problem. keep looking and digging. sometimes google search is better than a search in this forum. the forum search engine sucks! I'm looking too.
look for thread "acer aspire 5315 shuts down" by nvance nov 5 2007
good luck

---

### Post by bth73 on 2010-05-04
found thread and maybe bios update fixes but I doubt it .
I can't even get into bios cause bios is F2 and so is ubuntu boot menu. So, all I get is the boot menu.
I suggest selling the asscer and getting a real laptop.
I'm waiting for a reply from asscer.

---

### Post by gchand7 on 2010-05-04
My Acer 5920 works great with 10.04

---

### Post by bsmith1051 on 2010-05-05
sounds like a bad fan, one that is 'sticking' and can only spin-up if the computer applies full-voltage (like it normally does at power-up).  So, during normal usage the computer initially spins-up the fan (work ok), then shuts it off because the temperature is ok. But then, as the temperature increases, the operating system (and this could be true for Windows OR Linux) tries to slowly ramp-up the fan speed ... except that the fan sticks for anything less than full-speed / full-voltage.

So I would call Acer and tell them you have a bad fan, that it NEVER spins-up.  Make them tear it apart and replace it?  or, if it's out of warranty (probably?) then it's up to you to replace the fan.

That's my guess!
________

Or, there might be a way to manually control the fan speed and then you could set it to run full-speed and/or slow it down after manually getting it started?

---

### Post by FreeRide23 on 2010-05-19
Problem solved...

It was a Bios Update.

I have installed a fresh Windows on a other hard disk (SP2+SP3+Driver no other software) and maked a BIOS Flash to vs 1.45...

Problem solved. No overheating, no shut down, temp monitoring in Ubutunu funktions well.

Have a nice day.

---

