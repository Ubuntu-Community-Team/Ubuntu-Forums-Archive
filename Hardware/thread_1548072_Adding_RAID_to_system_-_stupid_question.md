---
title: "Adding RAID to system - stupid question?"
date: 2010-08-07
forum: Hardware
---

### Post by jayemee on 2010-08-07
Hey there,

I'm not sure if this is a stupid question or not, because I really don't know that much about it, but I'm fed up of having hard drives die on me, so I thought I'd do something about it. So I was going to convert an old dell desktop into a NAS, but then I realised that my current set up has 3 unused SATA ports on the mobo, which got me wondering...

So I'm currently running lucid off an old 80gb IDE HDD as my primary boot, with a 1tb SATA drive acting for storage (not my ideal choice, but I just could not get it running any other way). My question is: is it possible/feasible/easy to add another 3 SATA drives, and then convert all 4 drives into RAID, which I think would make it RAID 5 (not sure though, like I said, not too sure about all this!), WITHOUT having to set it up and start anew with a clean install. Googling around the topic seems to produce hits of people who already have RAID setups and are troubleshooting, so I thought I'd probe the wise bods here before ordering any parts.

Ooh, and I realise even if this were possible I'd likely lose all data on the drive currently installed, but that's easily backed up :) Just if I have to recover data from another drive I might have to disown technology and go live in a cave.

---

### Post by dmwahl on 2010-08-18
You should be able to create a RAID-5 array with 3 drives, copy everything over from the original one, then grow the array and add the first one again. If it were me I'd still have a backup, but it should be a reasonably straight forward process. Let me know what you end up doing.

---

### Post by Fafler on 2010-08-18
It's pretty straight forward. But follow guidelines closely and make sure you know what you are doing.

---

### Post by bogustrumper on 2010-08-18
Since you're thinking about using 4 drives, if you're worried about performance you might want to consider RAID10 instead of RAID5.  Gives a tiny bit more fault-tolerance, too; ie, RAID 10 can (sometimes) handle two drives failing (if it's the "right" two drives), while RAID5 cannot.

If you're losing a lot of hard drives in the same computer, you might want to think a little more about whether the hard drives are the problem.  If your computer has temperature problems, for example, then adding more hard drives to the case might just make that worse, and your drives will die sooner.

---

