---
title: "[SOLVED] help understanding swap / memory?"
date: 2008-11-14
forum: Hardware
---

### Post by alisonjo2786 on 2008-11-14
My very vague understanding of the "swap" thing isn't cutting it, so if anyone can explain it for me, I would very much appreciate it.  I did a little Google-ing but couldn't seem to improve the vauge understanding I currently have.

**Specifically**, I want to understand why I have about 0.5 GB Memory and 1.5 GB Swap.  I did not set up Ubuntu on my laptop, in case that wasn't obvious already... My boyfriend did it, and I've been learning from him and teaching myself as I go along, and it's frustrating sometimes but I think I'm doing ok.  ANYWAY, he's out of town, haha, and I'm pissed at how slowly my laptop is running, and the extra RAM I ordered hasn't arrived yet, and there may be nothing I can do, but I don't get why I only have 494 MB Memory and 1.5 GB Swap, and when I look at the System Monitor, most of the Memory is being used but only a small bit of the Swap is being used.

So, this may be really dumb of me, but I would love any explanation anyone can offer.  Thank you!!

---

### Post by Zack McCool on 2008-11-14
Well, you have 512M of memory because that's what's in the system...   You have 1.5G of swap because that's what was chosen when the laptop was set up.  Honestly, both of these are the best possible answers I can give...

As to why your laptop is slow, using all the memory but very little swap, that is something I can explain a bit more...

Applications cannot run in swap.  Swap is space on the hard drive where inactive stuff is pushed to free up memory for those things that are active.  You want the usage of this space to be as minimal as possible.  Hard drives are much slower than ram, so the more you are swapping things in/out of RAM, the slower your machine will run.

For the most part, the OS will not move things to swap until it has to, ie: your RAM is full.  This would explain why your swap is only a little used while your RAM is full.  The more the swap is used, the slower the PC will run.

So, what can you do to speed it up?  Not a whole lot, other than waiting for the additional memory to arrive.

You might want to look over (carefully) the output of htop, and sort it by memory usage.  Depending on what you have running, you may be able to kill some stuff off that's not horribly important to free some RAM, and therefore see some speed increases.

---

### Post by alisonjo2786 on 2008-11-14
Thank you so much, that was very helpful!  Hopefully I'll get my extra RAM early next week :)

One last question - what is htop?

---

### Post by baeksu on 2008-11-14
According to Wikipedia, htop is: "an advanced, interactive process viewer written for Linux." [link](http://en.wikipedia.org/wiki/Htop)

It's basically an improved version "top", and it's really handy to see which process are using your cpu or ram at a given time.

---

### Post by alisonjo2786 on 2008-11-14
Thank you!  I found it in Synaptic.  Thank you for the help.

---

