---
title: "RAM Speed issue w/ Optiplex GX260"
date: 2008-07-31
forum: Hardware
---

### Post by aristotlewilde on 2008-07-31
So I picked up a Dell Optiplex GX260 for next to nothing last week.

It came w/ 2x256mb of PC2100 (DDR266) memory.  

I had a few sticks of PC3200 DDR400 sitting around, so I figured I'd just toss in a stick or two of that.  

But when I removed the two sticks of PC2100 and added the PC3200, my system hangs at boot (either hangs on splash screen or hits initial tan screen before GDM and freezes).  This happens whether I have one or two sticks of DDR400 populated.  

The odd thing is, when I leave a stick of PC2100 in there and add a stick of PC3200 in slot 2, everything boots fine.  

Has anyone else seen such an issue?

*edit  Just upgraded to latest BIOS.  Still having the issue.

---

### Post by aristotlewilde on 2008-08-16
As an update, everything was fine for a bit.  Not being able to leave well enough alone, I actually ordered up 2x512mb sticks of PC2100 from Newegg to at least add some pep.

The two sticks that were meant for my machine specifically caused kernel panic though??.?.?.?

So I dropped back down to the 768mb that had been working, and I am fine. 

Windows installed fine for me though (did it to test).

I am chalking it up to finicky hardware.

---

### Post by captainfepa on 2008-09-25
Aristotlewilde: I have a few cheap SX260s for low powered tasks - one, for example, fits nicely in a kitchen cabinet to support recipes for wife. They each have one 512-MB 266MHz DIMM, and like you, I have been considering upgrading them - but after reading your post I have second thoughts. I thought to go to two 1GB DIMMs of PC3200 or PC2700, which I can get for no more $ than PC2100, although I see no way to adjust RAM speed. So: did you do any further experimenting? Are you sure the PC3200 you tried were low-density/Industry-Standard devices for the proper voltage? Is that 2.5V? I can believe almost any quirks attributed to Dell systems. I have enough SX260s to at least try moving two 512MB 266MHz DIMMs to one system, but first I'd like to hear of any further experiences trying larger capacity or faster RAM. Thanks.

---

### Post by Lord Xeb on 2008-09-25
The voltage of the ram and the frequency. Does you bios support stepping? If it does, it should step the clock speed of the ram down.

---

### Post by aristotlewilde on 2008-09-25
I actually got really tired of experimenting.  The RAM was standard no high density Ebay junk.  

Finally, I traded PC's w/ my daughter.  She lieks the quietness of the Optiplex (dropped XP on it), and I like that Ubuntu runs w/o issue on the self-built AMD system.  

There seems to be no rhyme or reason to why Ubuntu wasn't running properly.  I took the easy way out.

---

