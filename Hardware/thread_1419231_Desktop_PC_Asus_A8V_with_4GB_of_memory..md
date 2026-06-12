---
title: "Desktop PC Asus A8V with 4GB of memory."
date: 2010-03-01
forum: Hardware
---

### Post by momist on 2010-03-01
Hi there,

I'm running an Athlon64 X2 2GHz (Manchester core) on an Asus A8V motherboard.  This MoBo permits dual channel memory to be used, and supports up to 4GB in two pairs, i.e. 4 x 1GB DDR400 PC3200.  I've bought a set of similar (not "matching") Kingston Value Ram.  This, like the motherboard and processor, from eBay.   My problem is that when all four are installed, I get segmentation faults on a random selection of programs (not all).  This is when running the memory at it's rated speed and timings.

The programs that commonly display the problem are Rhythmbox, Terminal, and the game Gweled, although others sometimes throw faults as well.  The symptom is the program trying to start for a few seconds, then just dying.  When Terminal has been working and I use it to start a program, I can see the error "segmentation fault" with no other feedback.  A secondary unfortunate effect is occasional corruption of my hard drive contents, not very healthy for my peace of mind.

The strange thing is that with all the memory installed, it checks out as good using Memtest84+, and it works flawlessly with any two random pairs installed, just not with all four.

Can anyone suggest what to try next, to track down what's going on?  Are there any logs I should be looking at?

I'm getting close to selling these four again, and reverting to only 2GB permanently.

Thanks.

---

### Post by Schotty on 2010-03-02
Is this a fresh install?

I would find an extra hard drive and do a clean install on it and see how things work out for you.  Also another thing, is when you run memtest, make sure that you let it run for DAYS, as I have found heat can sometimes cause some goofy errors that only crop up after a long while of running.

If it still does that I would see if disabling dual channel works out for you.  Dual channel should, but isnt guaranteed I suppose, act like hard drive raids -- the slowest module sets the speed for all modules.  If your dual channel implementation is flaky or just crummy, you will probably find problems like this arise.

Those are my three suggestions:
1)Disable Dual Channel
2)Run memtest alot longer
3)Try a fresh install on another drive

---

### Post by momist on 2010-03-02
> **Schotty said:**
> Is this a fresh install?

Those are my three suggestions:
1)Disable Dual Channel
2)Run memtest alot longer
3)Try a fresh install on another drive

Thanks for the ideas Schotty.  I would not have thought about trying the fresh install.  Mine is from December, when I bought the motherboard, but I have all sorts of other issues with bringing over my 'home' directory.  For example, whatever I do I can't get GoogleEarth to run.  I've a spare 6.5GB drive not being used, so I could try that and see what difference it makes.

Meanwhile, I'll leave MEMTEST84+ running overnight.

I'm not sure about disabling the dual channel, as I thought the advantage was in memory access speed?  However, it is worth trying to see if that is the cause.  I'll let you know the outcome here.

Cheers.

---

### Post by momist on 2010-03-03
I said I would report back, and here it is.

I have made a fresh install of Ubuntu Karmic 9.10 from my alternate CD AMD64 on an old hard drive.  Testing with that install, and 4GB memory, I can obtain segmentation fault regularly (but not always) when starting gedit, same-gnome and some other programs.  Lots of programs run happily without seg. faults.  If I remove half the memory, I cannot obtain a seg. fault.

This is straight away from a cold start, and it doesn't seem to matter whether I have a lot of programs running at once, or just the problematic ones.

Memory configuration:  I have tried this with the memory latency set to 'Auto' (apart from having the speed set to 'Limit' in order to force 200MHz bus for 400MHz DDR), or with the latency set to the correct values for the Kingston sticks.  I have also tried it with and without the Bank Interleaving and Node Interleaving at Auto or Disabled. I think this turns on or off the Dual-channel feature, as I can find no other way to do that. There seems to be no difference.

Finally, I have run Memtest86+ v2.11 for 18 hours which gave 12 passes with 0 errors.

I have now removed all the Kingston memory, and reverted to my earlier 2GB from a different manufacturer.  I do not believe the memory is at fault, which leaves:
1.  The processor memory management.
2.  The mother board.
3.  The operating system.

Which is at fault?  I don't know how to find out, without a huge financial outlay for spare parts, (and a copy of Windows maybe).

I would welcome any other ideas please.

Thanks for looking.

---

