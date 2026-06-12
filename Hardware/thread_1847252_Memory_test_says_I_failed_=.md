---
title: "Memory test says I failed =\"
date: 2011-09-20
forum: Hardware
---

### Post by lifelike27 on 2011-09-20
I a very stupid mistake...

I pulled out my power cable from my laptop while it was still on (running a hackintosh at the time). I didn't have my battery in at the time so it completely powered off.

I have a triple boot system working here (Win 7, Ubuntu and OS X). Windows 7 did a chkdsk and now it boots up into my user but after a few seconds it restarts. OS X (I don't really care about but I'm still going to mention it) doesn't boot at all giving me an error saying kexts couldn't be loaded. Ubuntu (ALL HAIL!) works! Boots fine after multiple restarts not sure for how long it'll work though.

I did a memory test from memtest86+ through grub and after leaving to test 3 times it said only 1% passed.

I know that memory failures mean that you'll have to get new sticks since they aren't fixable, but I wanted to know if this does actually mean my memory is dead.

I removed the sticks and swapped them around - still getting the same problem. I'll try to borrow some RAM from a colleague and see if everything works fine with that.

Any suggestions? I'll post back when I've tried another set of RAM.

---

### Post by lifelike27 on 2011-09-20
Okay, so I'm probably the luckiest sob in the world right now. I got them ALL to work fine and I'm not exactly sure why. This is what I did/understand:

I figured that since Ubuntu was booting up, it was using the non-corrupted parts of my memory to run (assuming it is my memory that was screwed up). In the System Monitor it still showed my 4GB of RAM available. So I figured I'd try to max out the RAM and see what happens. I opened every possible application available so that my RAM was up at 3.2 GB. 

Restarted and then booted into Windows 7, played a bit of Portal 2 to see if it would crash and restart at any point. Then tried the same with OS X - works!

I'll try another memory test once again and see if anything has changed there.

---

### Post by An Sanct on 2011-09-20
A power off, no matter how, should never-ever corrupt RAM, unless a lightning strikes your computer :) but I guess, you would notice.

IMHO, shutdown and charge the laptop to the max and everything should work then.

---

### Post by lifelike27 on 2011-09-20
> **An Sanct said:**
> A power off, no matter how, should never-ever corrupt RAM, unless a lightning strikes your computer :) but I guess, you would notice.

IMHO, shutdown and charge the laptop to the max and everything should work then.

That's what I figured as well. Since my Ubuntu partition was working, I ruled out a possible hard drive failure. The memory test showed errors everywhere so I assumed that was the problem.

Anywho, it seems to be working by some grace of the Greek Gods. I'll do a memory test again either way when I'm free.

---

### Post by An Sanct on 2011-09-20
If possible, perform a BIOS memtest

Normally it is omitted/disabled, but its still there for backward compatibility I guess...

I personally would also take the battery out for a few minutes (but that's just me ;))

---

### Post by lifelike27 on 2011-09-20
I can't find it within my BIOS. I did also reset my BIOS to default settings, forgot to mention that earlier. I don't quite see how that would have affected it since I've never made any changes to it before.

Is there a particular way to perform a BIOS memory test?

---

### Post by An Sanct on 2011-09-21
That is BIOS dependant :) if you don't know, what I'm talking about with the "BIOS mem test", its that counting of available ram at startup.

I see no great functionality in that (since my 486 16mb ram machine), but it is still hanging there ...

---

### Post by Grenage on 2011-09-21
The BIOS memory count is just a count - it does no testing of memory.  Memtest is what you use to rule out memory problems, and you need to leave it for a _long_ time to get worthwhile result.  When I'm testing memory, I'll leave it for at least three hours.

The most probable issue is hard drive corruption, but a defective power supply is not out of the question.

---

