---
title: "RAM Installation"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by boomklever on 2007-01-31
This is not an Ubuntu/Linux specific question, so I hope that I'm right here.
Even though I've been using Linux for a few years now, I must admit that I'm still a complete hardware newbie, i.e. I can cope with some simple tasks like installing a new CD drive but that's about it.

Now I've ordered two 128 RDRAM modules from eBay. I've made sure that the specifications for my computer (or mainboard) are right - the important thing here seemed to be the number entitled with `P/N' (402824-722 for my system).

I've got two slots on my mainboard - one filled with an existing 128MB RAM module and the other one with what appears to be some kind of placeholder module called 6-Layer CRIMM, which must be in place if only one of the two slots is filled.

So, when my new RAM modules arrive, I figure I will have to remove the two existing modules (the real one and the dummy) and replace them with the ones I've ordered (in fact I could leave my old 128MB module but I suppose it's best to use only the new ones to rule out compatibility issues).

Will the computer automatically detect the new RAM modules or will I have to change anything in the BIOS configuration? Is there something I should watch out for?

Any help will be greatly appreciated.

boomklever

---

### Post by vigleik on 2007-01-31
If you install the hardware correctly, it should just work. The computer detects the amount of RAM (among other things) every time you turn it on, for precisely this reason.

---

### Post by az on 2007-01-31
Ubuntu ships with a useful tool called memtest86.

You can boot into memtest through grub or even just throught the live cd.

Memtest boots and only occupies the first few Kb of ram and is able to do extensive tests on your ram.  This is different than the "ram test" that usually happens when you boot a computer.  That test only checks for the presence of ram ano not whether it is working.  You will often find that you can stick in a few sticks of incompatible ram and it will pass that test, but memtest will reveal that only one of them can be  used.

To boot your OS with such bad ram can (will) cause your computer to crash.

So, stick in the new ram and then boot memtest before you continue on.  Let memtest run through a few passes (some of the later test take a long time, like writing to ram and then checking the pattern a half-hour later to look for changes.)  If you get no errors after the first few passes (five or ten minutes) your ram should be fine.  If you are using the computer for mission-crittical stuff, run the test overnight.

---

### Post by boomklever on 2007-01-31
> **azz said:**
> Ubuntu ships with a useful tool called memtest86.

You can boot into memtest through grub or even just throught the live cd.

Memtest boots and only occupies the first few Kb of ram and is able to do extensive tests on your ram.  This is different than the "ram test" that usually happens when you boot a computer.  That test only checks for the presence of ram ano not whether it is working.  You will often find that you can stick in a few sticks of incompatible ram and it will pass that test, but memtest will reveal that only one of them can be  used.

To boot your OS with such bad ram can (will) cause your computer to crash.

So, stick in the new ram and then boot memtest before you continue on.  Let memtest run through a few passes (some of the later test take a long time, like writing to ram and then checking the pattern a half-hour later to look for changes.)  If you get no errors after the first few passes (five or ten minutes) your ram should be fine.  If you are using the computer for mission-crittical stuff, run the test overnight.

Very good, thanks for the tip. I use my computer for personal stuff only and make regular backups, so I think could cope with a crash as a worst-case-scenario. I will certainly run the initial memtest checks and then find out if the modules work okay in daily use.

Thanks, again. :D

---

### Post by boomklever on 2007-02-01
Update: Thanks for your help. My RAM arrived today and everything went smoothly. My system's noticeably faster now. :D

Thanks

boomklever

---

### Post by Trespasser on 2007-02-01
I just did a memtest on my 756 mbs of ram and it turned out well (no errors) but don't plan on doing anything on your computer for an hour and a half if you let it run thru 4 passes like I did. :). I pressed Esc as it started pass 5. I never dreamed it would take that long. Wonder how long a complete test would take?

Later.

---

