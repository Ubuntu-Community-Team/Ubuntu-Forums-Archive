---
title: "Random Crashes - Hardware related?"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by maniacmusician on 2007-03-04
Hi,

I just finished building a new system a couple of days ago, and of course, I've installed Ubuntu on it. But I've been experiencing random crashes...in the middle of a task (sometimes cpu-intensive, sometimes not), the computer will just completely freeze up. I can't get any response (sometimes I can get the Num Lock/Caps Lock keys to turn on and off, but only sometimes). 

Since this was my first complete build, I'm thinking this may be a hardware problem; especially because the tasks I was doing while it crashed don't seem to be related to one another. Sometimes I'll get two crashes within the hour, sometimes after a few hours. It really does seem random.

So what I want to know is how can I target this problem and get to its root cause. Would any more information from me help? Do I need to run memtest for a few passes? Just wondering how I can get to the bottom of this, quickly.

Thanks.

edit: Oh, and I haven't done anything special to the system yet. No overclocks, playing with RAM settings, or anything. 

the RAM, however, seems to me to be the most likely culprit here (gut feeling). [This is the model of the RAM]("http://www.newegg.com/Product/Product.asp?item=N82E16820231085"), and I have two sticks of it. It is also supposedly in Dual-Channel (didn't check this). The settings for the RAM are still at the stock, manufacture recommendation (5-5-5-15), but I've heard that it runs stable at 4-4-4-12 as well (haven't tried that either yet). Any help would be great

---

### Post by Mr. C. on 2007-03-04
Run an overnight memtest.  Random crashes often indicate hardware failure.  I'd suspect memory problems at first, but it could be other things.  Buggy disk or NIC driver's are commonly at the root of random crashes, but they are much more difficult to pinpolnt.  Hardware diags are simple to run.

Report back what you find.
MrC

---

### Post by maniacmusician on 2007-03-04
I ran memtest (from the memtester package), and it gave me this:

> 
maniacmusician@Alexis:~$ memtest 2G
memtest v. 2.93.1
(C) 2000 Charles Cazabon <memtest@discworld.dyndns.org>
Original v.1 (C) 1999 Simon Kirby <sim@stormix.com> <sim@neato.org>

Current limits:
  RLIMIT_RSS  0xffffffff
  RLIMIT_VMEM 0xffffffff
Raising limits...
Allocated 2147483648 bytes...trying mlock...Killed


That didn't seem conclusive. Then I remembered I'd seen a memtest option in the GRUB menu, so I rebooted and tried that. I got a bunch of errors just on the first pass! By the third pass, it had accumulated almost 500 errors. So this is obviously the problem, right?

So the next question is, is it the RAM or is it the motherboard? Really hope that it's the RAM.

---

### Post by Mr. C. on 2007-03-04
You've isolated the problem.  You cannot be certain if it is the memory, the timings, or the motherboard without further tests.  You could:

a) relax the timings
b) replace the memory with known good, or new memory and repeat
c) replace the motherboard and test against the seemingly bad memory

Steps b and c require restarting from your memtest again.

There may also be BIOS updates the solve memory/motherboard issues; be sure to rule this out as a problem.

MrC

---

### Post by maniacmusician on 2007-03-04
Actually, here's an update: That test was all wrong for some reason. I think it was because I rebooted right into memtest, and there was still data left in the RAM.

With this suspicion, I started memtest again from a fresh boot instead of a reboot. It went through one complete pass, and I got only 5 errors this time, on test 7.It's on the second pass right now, finishing up test 6. I'll wait for it to finish 7 before I post this...Ok, on this pass, test 7 gave me no errors. But about halfway into Test 8, I got over 200 errors. So I guess the RAM is still faulty.

As for your suggestions, I don't think I want to do C; I only have 1 other, old motherboard. I can try B with a stick of RAM that I used for a year. As for the timings...they're already pretty high. I mean, it's supposed to be able to run at 4-4-4-12. 5-5-5-15 is the "safety zone" manufacturer recommended. I was planning on being able to tighten the timings.

So, I have to do a BIOS update as well? :) pain in the ***, since I'll have to install a floppy drive now. Ah, well. It happens. So, I'll go test with another stick of RAM first, and then I'll do some BIOS updates. 

anything else?

---

### Post by Mr. C. on 2007-03-04
> **maniacmusician said:**
> Actually, here's an update: That test was all wrong for some reason. I think it was because I rebooted right into memtest, and there was still data left in the RAM.

With this suspicion, I started memtest again from a fresh boot instead of a reboot. It went through one complete pass, and I got only 5 errors this time, on test 7.It's on the second pass right now, finishing up test 6. I'll wait for it to finish 7 before I post this...Ok, on this pass, test 7 gave me no errors. But about halfway into Test 8, I got over 200 errors. So I guess the RAM is still faulty.

As for your suggestions, I don't think I want to do C; I only have 1 other, old motherboard. I can try B with a stick of RAM that I used for a year. As for the timings...they're already pretty high. I mean, it's supposed to be able to run at 4-4-4-12. 5-5-5-15 is the "safety zone" manufacturer recommended. I was planning on being able to tighten the timings.

So, I have to do a BIOS update as well? :) pain in the ***, since I'll have to install a floppy drive now. Ah, well. It happens. So, I'll go test with another stick of RAM first, and then I'll do some BIOS updates. 

anything else?


*Only* 5 errors!  0 errors is *required*.  1 error is enough to call off the game.  If there are errors on non-ECC chips, you cannot rely on that memory.  Game over.

Boot or reboot makes no difference.  The memory test doesn't care what bits where there - it writes and tests the read.

Fix your hardware.

MrC

---

### Post by maniacmusician on 2007-03-04
gotcha :)

It's testing the other stick of RAM I put in there right now. It already completed 1 whole pass without any errors at all; so should I assume  that my new RAM was defective or should I keep this test running longer? My new sticks of RAM already had 5 errors by this point, and this one has none.

---

### Post by Mr. C. on 2007-03-04
Personally?  I run for 24-48 hours.  I can wait the day or two, but I can't afford crashes, corrupted file systems, corrupted data, etc.

Be patient; be sure.

You can assume your sticks of RAM do not work with your motherboard; you can't assume the two models won't work together.   It is in uncommon for parts to be just on the edge of spec, and the unlucky pairing of those two cause failure.  Put one of the parts in another system, it might work flawlessly.

MrC

---

### Post by maniacmusician on 2007-03-04
since I have two sticks of RAM, I can't run memtest for 24 hours for each session, because this is what I've done so far:
> 
Two sticks of New RAM: Two complete passes, 800+ errors

One stick of older, working RAM: 2 and a half passes, no errors

Now, I want to find out of both sticks of new RAM are good or bad. So, I'm running memtest on them seperately.

> Stick 1 of New RAM: Running 3rd Pass right now, no errors yet. 
Stick 2 of New RAM: Not tested yet.


I was going to let Stick 1 run for about an hour or so more, and then try stick 2. So far, I'm pretty sure most, if not all of the errors, will be on Stick 2. Hopefully all, so I don't have to RMA them both. If nothing shows up after say 4-5 passes, isn't it safe to assume that there are no errors? Especially since most of the previous errors showed up so readily after just a couple of passes?

---

### Post by Mr. C. on 2007-03-04
This is a good approach.  Test stick 1, then stick 2, then longer combined.

Get comfortable with the notion that there are no definitive answers here - all you have are risk levels and confidence levels.  You have to judge for yourself how risk-tolerant you are.

If it fails, is 100% certain that the memory is not reliable.  If it passes, you can make no other conclusions that "it passed on this one test I did".

MrC

---

### Post by maniacmusician on 2007-03-04
I'm not going to test any longer for both of them combined; we already know it fails at that, so one of the sticks is obviously bad. I'm going to run Stick 1 for a while longer, and if by the end of the 6th pass, it hasn't come up with any errors, I'll be satisfied and move on to Stick 2.

Thanks for all the help.

---

