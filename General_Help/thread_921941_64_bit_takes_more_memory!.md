---
title: "64 bit takes more memory?!"
date: 2008-09-16
forum: General Help
---

### Post by claymater on 2008-09-16
Ok guys.. I just read somewhere that the 64 bit version on ubuntu takes up lots of memory... I have the 64 bit... How (if possable) do I "downgrade" to the 32 bit? (without losing data)

---

### Post by -Zeus- on 2008-09-16
I think whatever you read is wrong.

---

### Post by claymater on 2008-09-16
> **-Zeus- said:**
> I think whatever you read is wrong.

> **stchman said:**
> Are you using 64 bit OS?  If yes then that is a culprit.  64 bit OS uses a lot more RAM that 32 bit OS.



well this is what I saw from [this thread ]("http://ubuntuforums.org/showthread.php?t=859198")

---

### Post by oilchangeguy on 2008-09-16
> **claymater said:**
> well this is what I saw from [this thread ]("http://ubuntuforums.org/showthread.php?t=859198")

just because it is written, does not mean it's true. have you noticed a performance loss, before you found this thread?

---

### Post by mb_webguy on 2008-09-16
Well, a 64-bit OS *will* use more memory from a certain perspective, as it uses 64-bit chunks of memory rather than 32-bit chunks of memory.  If a program requires 96 bits of memory, then the system will have to use two 64-bit chunks (for a total of 124 bits) rather than three 32 bit chunks.

However, since all but the smallest programs use amounts of memory of at least several kilobytes if not several megabytes, the net effect is insignificant.  Also, a 64-bit OS processes more information in the same amount of time as a an equivalent 32-bit machine, so information needs to reside in memory for less time.

Think of it like this...  If you're packing things in boxes, you'll get things done faster if you have larger boxes, since you spend less time taping and moving boxes.  However, you may occasionally end up with a mostly empty box because you don't have enough stuff left over to fill it, which means you would have wasted less space using a smaller box.  But if you deal with hundreds of thousands of boxes a day, then the occasional partly empty box doesn't matter much compared to the increase in packing time.

---

### Post by howefield on 2008-09-16
It does take more memory, at least on my install it does. But that isn't a problem as performance is better.

One pleasing benefit is that kaffeine and firefox have yet to crash on me, but regularly did on 32 bit install, may not be directly related but I'm happy just the same. The only downside so far is some sites do not load video, eg cnn video, joox.net and most likely I just need to do more work to get them sorted. 

But to get back to the OPs assertion, I agree 64 bit needs more memory. (but nothing to worry about, unless you haven't got it) :lolflag:

---

### Post by claymater on 2008-09-16
Well I only read into that so much because I have 64 bit ubuntu, and that I have had to restart my computer like twice a day because it freezes all the time :(

---

