---
title: "[SOLVED] could my kernal be mis-reading my CPU?"
date: 2008-09-26
forum: General Help
---

### Post by Kain000 on 2008-09-26
Hey everyone, 
Just noticed whilst poking the system monitor of my server and noticed it's tracking load on two CPU's, witch nowadays with dual and quad core CPU's that's no surprise, however my server is packing a Pentium 4.  and as far as I know the intel duel core line was the first CPU die to feature 2 processing cores.  it doesnt seem to be causing any problems but I think it's strange that the kernal would misread this as it's just a hardware Identifier, and an old one at that. Whats odder is that the two "cores" in my pentium 4 that are being read are showing different loads, as if it were a dual core.  weird!  so anyway I was just curious if anyone had an idea as to whats going on.
-sean

---

### Post by Pro-reason on 2008-09-26
I don't really understand what you want.  You have a processor which has two cores (or performs [hyper-threading]("http://en.wikipedia.org/wiki/Hyper-threading"))... and you're complaining about it?  You want it to be as slow as a single-thread processor?

You can probably achieve that by tweaking your BIOS settings, but I don't know why you would want to.

---

### Post by jake1017 on 2008-09-26
My guess would be that you have hyper threading turned on. This is not a bad thing. Unless your application or OS is malfunctioning there is no reason to turn hyper threading off.

---

### Post by Peter09 on 2008-09-26
Just to clarify, Hyper-Threading is where a single computer 'pretends' to be two computers. It improves throughput a bit as different bits on the chip can be kept working while other processes are going on.

---

### Post by Kain000 on 2008-09-26
> **Pro-reason said:**
> I don't really understand what you want.  You have a processor which has two cores (or performs [hyper-threading]("http://en.wikipedia.org/wiki/Hyper-threading"))... and you're complaining about it?  You want it to be as slow as a single-thread processor?

You can probably achieve that by tweaking your BIOS settings, but I don't know why you would want to.

No i didnt want to slow anything down, It turns out that I have hyperthreading on and I didnt know that hyperthreading makes it apear as two different CPU's   I was only wondering why my single core P4 was looking like a dual core.

---

### Post by Kain000 on 2008-09-26
Jake and peter thanks for the clairfication I wasnt sure what hyperthreading really was.

---

