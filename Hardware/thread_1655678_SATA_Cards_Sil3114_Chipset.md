---
title: "SATA Cards Sil3114 Chipset ?"
date: 2010-12-29
forum: Hardware
---

### Post by pundip on 2010-12-29
I would like to add extra SATA slots to my desktop (10.04). I would like to do this in a manner that does not deprive me of my will to live. What I am looking for is sata card that is cheap and works out of the box that is I turn off my computer put in the card connect up a bunch of drives and turn it back and vola they are there when I click on My Computer. Not interested in RAID.  I have found a SIL3114 based card. Has anyone had any experience with this card. Or is there another card out there that will give me more SATA slots with out the pain?

---

### Post by powleeno on 2011-04-21
ok, don't know if this will help, because I really have no term of comparison, but what the heck.

I'm currently fighting a Gigabyte GA-6VXE7+ because of a sata board with that same chip, the sil3114. MoBo has a pentium 3 at 600 mhz and it's older than hell times two; pci-board manufacturer's site provides windows drivers for raids and stuff alike dating from 2010, but linux support is scarce and it sums up to "go to [http://kernel.org/](http://kernel.org/) and try something you can think of; good luck" and that dates from 2003.

I've been fighting it because every now and then it complaints about input/output errors, but then again at turns it functions correctly.
earlier this dawn it had a completely erroneous behavior and even though I was beginning to suspect that it could be hardware, I looked the other way because ubuntu kept saying a partition was corrupted so I thought that could be it. I lined up for the data recovery song and dance (which took a few rather bumpy hours) and scared me sh#$less as it threatened to have lost all (yes, all) my music collection. after a few fscks and a fresh os install it seemed to work correctly and mounted everything, but then it went buggers again, this time regarding another hd mount.
hard drives like a good laugh as much as the next bloke, I guess, but they don't just have a collapse-driven-fetish so I'm definitely betting on hardware issues this time (pci to MoBo and so on).

I am now having a cup of coffee and a cigarette and stashing as much of stamina and good will I can before daring into updating all of the hardware's software, drivers, bios, whatever untill this sucker either works or blows me out of the ring.

how does this help you and why would you want to know? well, 1: it doesn't, really, but 2: it might help to prove that if you do run into any kind of stress it might be because your hardware is as old as mine, because ubuntu does see the satas fine if you run ```
lshw -c disk
```. they're just waiting to be mounted and reported to fstab. in case your hardware is a bit more fresh you might even go hustle free. of course, then again, who knows?

---

### Post by MikeKulls on 2011-11-23
I just installed one of these cards and it is working straight off pretty much (just had to run updates). I will report back if I get any issues.

---

