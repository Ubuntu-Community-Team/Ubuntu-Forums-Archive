---
title: "RAM problem"
date: 2008-11-14
forum: General Help
---

### Post by vapd on 2008-11-14
Hi, I put together a few old spares to make an Ubuntu based rig and just to be on the safe side, I hadnt used the board or RAM for years, I ran memtest from the ubuntu CD. It picked up errors on the first pass on both sticks. The system is a 2000xp palamino, Abit Kr7a 133r, GF2MX AGP and a 400 and something watt Enermax PSU. I have stripped it down to just that and a dvd drive. The RAM is one stick of standard Crucial DDR333 and one DDR400.

The really crazy thing is that the same RAM works fine in an Abit An7 that I have running Mythbuntu. I took the RAM out of that board and stuck the Crucial in let one stick pass two passes of memtest and the other 6 passes. Even crazier this was at DDR333 and DDR400 speeds. Whilst running at 133 bus in the older kr7a 133r with really relaxed timings (fail safe defaults) it gives errors.

I am stumped why neither crucial stick will work in the older board but will work in the newer. Any ideas?

---

### Post by prshah on 2008-11-14
> **vapd said:**
> 
I am stumped why neither crucial stick will work in the older board but will work in the newer. Any ideas?

Clean the memory slots on the older board. A few pins maybe rusted. You can use a cotton swab dipped in IPA (Iso-Propyl Alcohol) to _gently_ wipe the pins in the memory slots.

Giving it a good cleaning with an industrial blower or a vacuum cleaner set to _blow_ (_not_ _suck_) will also help a lot.

---

### Post by vapd on 2008-11-14
Thanks for that advise! I have used compressed air on the board and done a close visual inspection of the memory slots and cant see any signs of corrosion. I dont have any  IPA, I have found it tough to get hold of it in the UK. Chemists will sell it but its not electronics grade stuff its a lower grade I have been told and has more impurities than electronics grade IPA. I dont know if that matters in this instance? Anyway I have some Arctic Silver Thermal Surface Purifier, I suspect its the same stuff or will do the same job?

Anyway I have done some more testing. Not sure what to make of it. The Crucial RAM tests fine at 100 bus in the Kr7a 133r but as soon as I stick it up to 133 (and this is DDR333 and 400)it falls over quite quickly in memtest. I have tried 3 of the 4 DIMM slots at 133 bus and slot one and three the test lasts about 10mins before failing in slot two it lasted less than 30 secs before failing. Slots one and two both pass at 100mhz. So does this point towards dirty or corroded slots or something else?

I probably should have said before that I also have a standard Abit Kr7a (this one was rescued from death by a hot swap BIOS flash so I am not entirely sure about it, one day it worked fine and then without anything untoward happening it just ceased to post so I did the hot swap bios flash in an old Asus P2B and it then worked but I never stress tested it I just stuck it in a box). Anyway this Kr7a I dug out a few months back and using the Crucial RAM that I am currently struggling with I installed Ubuntu and then got some problems so I ran memtest on that setup and found exactly the same problem. The ram would test fine at 100mhz but at 133 it failed in about 10 mins. I was using the same CPU as I am now using in the Kr7a 133r.

I am unsure if this helps diagnose the problem or not!

:confused:

---

### Post by kerry_s on 2008-11-14
you know running the wrong ram can fry the board?
[http://www.sharkyextreme.com/hardware/motherboards/article.php/10703_1008771__4](http://www.sharkyextreme.com/hardware/motherboards/article.php/10703_1008771__4)

> Memory

    * Four 184-pin DIMM sockets support PC1600/PC2100 DDR SDRAM module
    * Supports 6 banks up to 3GB DRAMs for unbuffered DDR/SDR modules
    * Supports 8 banks up to 3.5GB DRAMs for registered DDR/SDR modules 



---

### Post by vapd on 2008-11-14
Hi, as far as I can make out I am not running the wrong RAM. I know the RAM is potentially faster than the board is designed to take but it has not been run at faster than 133mhz. And the board is made to take 133mhz CPU's and RAM.

I looked through the review in the link you posted but couldnt find anything about using DDR333 or 400 frying the board.

I have recently stuck the Crucial DDR333 and DDR400 back in the rig in slots 1 & 2 and memtested it again running the FSB at 100, no surprise it passed.

I guess that for the time being at least I will only be able to run the rig at 100mhz.

---

