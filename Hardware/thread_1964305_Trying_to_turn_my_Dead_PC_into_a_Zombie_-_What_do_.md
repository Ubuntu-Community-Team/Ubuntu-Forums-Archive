---
title: "Trying to turn my Dead PC into a Zombie - What do I replace?"
date: 2012-04-23
forum: Hardware
---

### Post by ewangr on 2012-04-23
Have been running my Asus CG5290 Desktop (Core i7 920, 9 Gigs Ram - 3 2GIG DDR3 and 3 1GIG DDR3, nVidia GeForce GTX 260, 1TB Internal Drive) on Ubuntu 12.04 beta 2 64-bit for a few weeks because it had been having problems with Windows that seemed specifically timed to an nVidia driver update. In retrospect I'm glad I switched anyway, but I may have blamed Windows for a problem that wasn't it's fault.

In any event, yesterday I had some disk problems where the main drive kept going into Read-Only mode. I finally shut down the system, and opened it up to notice that the video card was in the slot nearest the processor and a couple other heat sinks. Given that I had seen continuing issues with applications freezing (gray screen and then later coming back) I suspected overheating. I went to move the card... and evidently pushed down a little hard breaking off the "latch part" of the PCI-slot. Which meant now I HAD to move the video card.

There is one other slot on the machine where the card can fit, but it isn't a perfect fit as it latches down, but appears a bit loose. There is another "regular" PCI slot right next to it, and I suspect it is just high enough to be keeping the video card from completely seating.

By going into "manual" mode I was able to reboot the machine, and had to clean up a lot of messed up inodes. The computer will work as long as it's laying on it's side (which minimizes any stress on the video card), but it's kind of a big box to leave that way.

Not having budgeted to replace my PC, I'm thinking I should be able to replace the bad "part" - but I'm not sure which part that would be? Suspects are obviously the Motherboard, the HD, and the Video Card. Memory survived a full Memtest test, so I'm suspecting that's ok.

Am also worried that if I pick the "wrong" part I may have the same problems or worse, and kill the "new" part. IOW, if I replace the video card and it's actually the HD going bad, it may be loading a corrupted driver that would kill the new card. Of course if it's just a crappy motherboard (as the design and the slot fragility imply), I could be frying a new anything for that reason.

Any thoughts on how to narrow down the likely culprit so in a week or so when I can afford to replace one of them, I can be fairly certain I'm replacing the right one? I mentioned the model and specs above in case there are known issues with Ubuntu that weren't obvious.

Help me Ubu-wan-kenobis... you're my only hope!

---

### Post by Bucky Ball on 2012-04-23
You haven't mentioned the PSU. Is it of decent quality or a generic silver box? Your issue could be any number of things, though, yes ...

---

### Post by ewangr on 2012-04-23
It's a 484 watt power supply according to the documentation. I will try to take a look the next time I open it to see if it has any labels, but I'm going to presume it's nothing too special. I do keep the machine plugged into a UPS full-time to minimize the hits, but of course that's no guarantee if the PSU itself is going...

---

### Post by ewangr on 2012-04-24
So I'm running out of ideas of what to check. Ran Palimpsest and the HD keeps coming up clean with no S.M.A.R.T warning or any further bad sectors. Have had none of the "gray" screens, and in fact other than the missing latch on the one PCI slot, the system seems to be running better than ever.

Part of me thinks that this is just telling me that while the box is kind of HUGE to leave laying down, that if I am willing to make that compromise I have nothing to worry about. Part of me thinks I'm just in the calm before the storm.

Should I consider myself to have had a bad couple of days and just move on? Anything you can suggest that would give the other system components the same type of exercise that Palimpsest and MemTest run that might help me determine what (if any) component is the weak link?

---

### Post by ewangr on 2012-04-25
So later in the evening it seemed that my screen kept turning grey every time I had to hit the network or the hard drive. So that made me suspect that even if the hard drive tests indicated it was just fine, that possibly there was still some issue. It's a 7200 rpm drive with 32 mb of cache, and so it occured to me that it could also be that perhaps there's a cache problem... or maybe even something odd with the motherboard and the built-in SATA controller. Part of the reason I keep suspecting the motherboard is that the on-board audio died about a year ago. No big deal since i got a USB external card from Creative, but given that there was no obvious reason for it to stop working...

Before I went to bed last night I turned the computer off. When I got home this evening I turned the machine on, and the video kept blinking off and then on for a minute or so, and then flick off and back on, etc. Shut it down, opened the box, confirmed nothing seemed to have sparked and the card wasn't too hot to the touch, turned it back on, and it's been rock-solid since.

I can only afford to replace one component at this point. Which one would you recommend as the best first choice? I'm thinking motherboard, then HD, then video card... but I could also argue HD, then motherboard, then video card. Or maybe... ?

---

### Post by ewangr on 2012-04-26
OK, so I left the machine running all day with the System Monitor on to see if I could see any overheating. Temps at the time I got home looked fine, BUT I noticed that the SB Max temp claimed to hit 255C at some point during the day. Any idea what that could be about when none of the other temps went over 65C? I'm thinking that REALLY means MB issues, but am I right to think that?

---

