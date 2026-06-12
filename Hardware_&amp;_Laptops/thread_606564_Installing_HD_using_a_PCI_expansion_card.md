---
title: "Installing HD using a PCI expansion card"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by xzing on 2007-11-08
I just installed gutsy on my old Frankenstein computer and I can't get the two hard drives I have connected through my PCI card to work.  When I connect one or both of the drives the machine starts and takes an extremely long time to boot.  Once it finally does I can't see the drives anywhere.  Then when I shut it down I get a ton of error messages telling me I have HD errors.

I don't buy those errors because the drives are pretty new, I have barely used them and they were working just fine a week ago.  So I am guessing there is some PCI Ubuntu voodoo I am missing out on here.

So for anyone who is interested in helping me get these drives up and running the info on my machine is right here:

AMD Athlon 2.5 GHz
1 GB of RAM
two 40 GB drives (workin' just fine)
on board sound and video

PCI Expansion card is a SYBA SY-VIA-150 PCI SATA/IDE combo controller card non RAID.  The two drives I want to get up and running are both 250GB Seagate.

If anyone can give me an idea of what to do to get these drives working I would appreciate it.  Could the driver for the PCI card be wrong?  Is there some magical Ubuntu thing I have to do this time around that I didn't have to do last time?  I have been working on this particular problem for about 4 days now and at this point am ready to blowtorch the thing and just take it as a loss so any info would be appreciated.

Thanks in advance!

Xzing

---

### Post by xzing on 2007-11-16
For those of you who have looked at this and not been able to help and also for those of you who may have similar problems I want to include some further info.

First of all the two drives I spoke of are both Maxtor drives (apparently owned by Seagate now).  They are DiamondMax 21 both 320 GB.

I have played with this some more and this is what I have found out.  When I connect the drives directly to the IDE connection on the motherboard they can be seen and the small amount of data I have put on them is in fact there.  However when I connect them through the PCI card they still cant be seen.  But the caveat is that when I connect my other drives (both Maxtor) to the PCI card those drives can be seen.  So the problem seems to lie in those particular drives being connected to the PCI card.  Under Feisty Fawn I had no problem with this but under Gutsy I seem to have the problem.

So I guess my only course of action is to connect those drives to the motherboard and connect my other smaller drives to the card and just reinstall the OS on one of the larger ones.  This of course drives me crazy because it is still not an answer to my initial question.  Why is the PCI card all of the sudden not liking those particular drives, is it a difference in Gutsy vs Feisty?  What will happen next time I upgrade, will I have to go back the other way?  This seems very odd to me.

Perhaps this will help others understand the overall problem, as for me I am still stumped.  I guess Gutsy, Maxtor DiamondMax 21, and SYBA SY-VIA-150 just don't play nice together.

---

