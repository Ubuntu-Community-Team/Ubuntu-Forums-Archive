---
title: "[Solved] Hardware problem"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by c.dric on 2007-01-10
i have this strange problem with one of my computer :

Today, while i was in Xfce it just froze ...
I reboot, it freezes again only after a min when i am in GDM ...
I re-reboot and go into the Bios screen for a clue ... it freezes after a few minutes.
The last times i tried i couldn't get to the bios :-? 

The situation now : 
The computer powers up, the cpu fan (controlled by the MB) works, the cd drive led blinks a few times (as usual), the hdd led stays on (unusual) and that's it ... nothing else.

Anyone know which hardware could be responsible ?
Thanks.

PS : The last time i could get in the bios the cpu temp was at 38C/100F which is usual. 
I didn't overclock and it didn't smell like the cpu burnt.

---

### Post by futz on 2007-01-11
Hooboy! This could be a fun one to troubleshoot. Do you have a spare power supply (PSU)you can swap in to eliminate that as one possibility? If not, you can pick up a dirt cheap oem one at your local computer store to test with.

Check the PSU fan. Still working? Or is it stuffed with dust and/or seized up?

How about the CPU heat sink? Is it stuffed solid with dust and fuzz? If so, even with the fan working it might not be cooling at all. An overheating CPU could cause symptoms like you describe. I know you said the BIOS said 38, but look anyway. Might take a minute or two to get hot enuff to shut down (crash).

Another thing you could try is unplug the box and clear the BIOS by jumpering the Clear BIOS pins for a second or two. Then put the jumper back the way you found it, plug in and power up. If that works and you can POST, your BIOS will be set to all default settings, so you'll have to go thru the BIOS and make all necessary changes to suit your system.

Reseat the RAM. Unlikely, but possible. Also unlikely but possible is a failed RAM stick.

---

### Post by c.dric on 2007-01-11
The PSU ([Antec Neo HE]("http://www.antec.com/ec/productDetails.php?ProdID=09150")), the heatsink ([SI97a]("http://www.thermalright.com/a_page/main_product_si97a.htm")) and the CPU fan ([Nexus Real Silent]("http://www.nexustek.nl/92mmcasefan.htm")) are all new. They were installed last week so dust is not an issue.

I'll try switching the PSU & RAM and the resetting of the Bios later today.
Thanks for your help.

---

### Post by Brunellus on 2007-01-11
thread has been moved to a more relevant support forum.

---

### Post by c.dric on 2007-01-11
> **Brunellus said:**
> thread has been moved to a more relevant support forum.

If you like. But this has nothing to do with Ubuntu.

---

### Post by futz on 2007-01-11
> **c.dric said:**
> They were installed last week so dust is not an issue.
I've seen (this was back in time a bit with different socket/cpu types) a heat sink get installed so it looked right, but it wasn't *quite* contacting the cpu heat spreader right. It was hung up on something and only touching the cpu on one corner. The machine would start and work ok for a minute and then crash as the cpu overheated. Guess the partial contact was allowing it to last that long, as they only last seconds without any heat sink.

---

### Post by c.dric on 2007-01-11
well it looks like it was a RAM problem after all ... 
(i hope it hasn't frozen back when i go check tomorrow morning)

what i did : 

- Tested with an old PSU: same problem
- Removed heatsing, cleaned & re-applied thermal paste: same problem.
- Set Bios back to default then i noticed one of the 2 ram stick of 256mb was listed as 32mb. 
I removed it and it works fine so far.

Thanks for your help Futz.

---

### Post by Brunellus on 2007-01-12
Thread marked "Solved."  Hope the new RAM works out!

---

### Post by c.dric on 2007-01-12
it's been 15h now and didn't have any lockups since then so that's good :) 

i do have another question while we are talking about RAM : 

If my cpu has a fsb of 333MHz, my best choice should be to buy DDR333 RAM right ?
Can i use a DDR266 ram stick with it if my card support both formats ?

This is what i've found in the mb manual : 

> Memory: 2 DDR DIMM Slots: DDR1 and DDR2
PC3200 (DDR400) for 1 DDR DIMM slot, Max. 1GB
PC2100 (DDR266) / PC2700 (DDR333) for 2 DDR DIMM slots, Max. 2GB

---

### Post by futz on 2007-01-12
> **c.dric said:**
> it's been 15h now and didn't have any lockups since then so that's good :)
Excellent! Your problem has been found.

> If my cpu has a fsb of 333MHz, my best choice should be to buy DDR333 RAM right ?
Not necessarily, and usually not. FSB is the Front Side Bus speed, which is multiplied up off the system clock. The RAM clock rate (and CPU) is also multiplied up off the same clock, but most often to a different clock rate.

> Can i use a DDR266 ram stick with it if my card support both formats ?
If you have multiple sticks of ram in the machine they must match in speed rating. Your board can run PC2100 **or** PC2700 **or** PC3200. Both sticks must be the same type. (You might get away with a mismatched pair, but you'd have to run both at the clock rate of the slower stick. And it's very possible that wouldn't work anyway because of RAM timing issues.)

So look at the good stick you have, see what type it is and buy another to match. Or dump it (use it in a klunker machine) and get yourself a pair of PC3200's. If the board does dual channel (interleaved) RAM then the sticks must match in size also.

EDIT: Oh! Just noticed your quote says PC3200 one slot only? Very strange! What mainboard is this? You might be stuck with PC2700 if you want two sticks. 

PC2100 won't be any cheaper than PC2700 or PC3200 if that's what you're thinking. Unless you're buying fancy premium RAM, the prices are pretty much identical. And PC2100 and 2700 are antiques (actually so are PC3200, but at least some mainboards can still use em).

---

### Post by c.dric on 2007-01-13
thanks for the tips. i think i'll go for a 1gb stick of PC3200 that should be enough for xubuntu :) 

the MB is a [K7VT4A+]("http://www.asrock.com/product/k7vt4a+.htm") and the CPU is an Athlon XP	2700+.

---

### Post by futz on 2007-01-13
> **c.dric said:**
> thanks for the tips. i think i'll go for a 1gb stick of PC3200 that should be enough for xubuntu :) 

the MB is a [K7VT4A+]("http://www.asrock.com/product/k7vt4a+.htm") and the CPU is an Athlon XP	2700+.
Those Asrock guys and their funny mainboards. :mrgreen: They're always doin something funky, with strange chipsets.

I have two of their mainboards in older spare boxes here (I have way too many computers). 

One is the ultra cheap and old-fashioned P4i65G - not much funkiness there. Just a vanilla all-in-one oem-style S478 board.

The other is the very odd 939Dual-SATA2 with Uli chipset and JMicron drive controller. Lots of weirdness for Linux users on that board. It can be a fight to get Linux installed if your configuration isn't just so.

Good luck with your new RAM.

---

