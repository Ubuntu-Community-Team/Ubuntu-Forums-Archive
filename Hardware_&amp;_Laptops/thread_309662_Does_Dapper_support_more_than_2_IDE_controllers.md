---
title: "Does Dapper support more than 2 IDE controllers?"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by lukon on 2006-11-29
Ya.

Does Dapper Drake support more than 2 IDE controllers?

SITUATION:

I want to use all 4 IDE positions provided by the 2 IDE controllers on the motherboard ... AND ... use the IDE controller provided by my "old school" Creative Labs CT2940 SB16 sound card.

Google browsing other info-boards reveals that Linux historically did not support more than 2 IDE controllers in the configuration I want. (Dedicated disk controller cards may have been the standing solution at the time - I don't know.) So waht I want to know is: has the situation changed? Has Linux evolved toward supporting more than 2 controllers by now?

---

### Post by Unterseeboot_234 on 2006-11-30
So, let me say right off the bat, I'm a noobie on Linux, BUT the IDE is a feature of BIOS. You see it loading up when the computer first starts, before it begins to seek out the hard drive.

---

### Post by lukon on 2006-11-30
If the IDE were purely a function of the BIOS, then any operating system would recognize all the available IDE controllers. But this is clearly not the case. On my dual boot computer here, Win98se recognizes 3 IDE controllers, 2 on the motherboard and 1 on the soundcard. But Ubuntu only recognizes the 2 on the motherboard. Therefore, IDE recognition is NOT purely a function of the BIOS. Operating systems must somehow also contribute to IDE controller recognition.

---

### Post by Johan! on 2006-11-30
I'm using a Promise Ultra 100 TX2 card in combination with the IDE controllers on my ASUS A8N-E motherboard.
So this works:) 

I'm not sure if the IDE controllers on the old soundblaster will work.
And if they work, they will be REALLY SLOW, i think...

---

### Post by lukon on 2006-11-30
Johan!

Is there an IDE device (or deviceS) connected to both your motherboard IDE controllers, or to just one of them?

If you've got a device on each controller, then I'd say it confirms that Ubuntu Linix can now recognize more than 2 controllers.

---

### Post by Johan! on 2006-11-30
I have 3 harddisks and 2 CD/DVD's in my computer, so I'm quite sure it will work ;) 

The only problem I can think of is 2 identical cards in 1 system...but that's not the case here :)

---

### Post by lukon on 2006-11-30
Heck ya. That confirms it.

My next sub-problem is to discover the next roadblock against making this SB16 soundcard IDE controller work. If Ubuntu CAN recognize that controller, why isn't it?

I suspect it may have to do with some kind of addressing conflicts or missing addresing data - something like that - that I hear happens with old ISA PNP cards like this. ...and isn't there a utility for adjusting addressing parameters on such cards? Hmmm.

---

### Post by Johan! on 2006-11-30
The SB card probably doesn't support
[LIST]
[*]Plug & Play
[*]Bus mastering
[*]DMA
[/LIST]

So it will not be easy to configure it, if it's possible at all.

If you manage to get it to work, it will be SLOW, and it will eat CPU cycles.

---

