---
title: "Gparted goofing around with me - Basic Partitioning!"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Aped on 2009-02-26
Super basic question probably but I already have an unused space reserved for my second (first, technically;) OS, ubuntu. However, GParted will only let me choose a couple of options. See screencaps linked below. 

Option 1, guided resize:

[img]http://img513.imageshack.us/img513/4405/failure1guidedresize.png[/img]

Option 2 I obviously don't want since I just installed and patched up XP Pro. 

Option 3, when highlighted, shows After: Ubuntu 100%, just like when I choose

Option 4, Manual, which does not in fact seem to be very manual at all. See image below. 

[img]http://img11.imageshack.us/img11/7375/failure2manual.png[/img]

Frustrating thing is, I can SEE the unused space reserved for ubuntu! It's right there! Let me format it as ext3 and be done with this crap! 

I don't have a lot of experience (obviously) with using gparted and haven't exactly installed ubuntu a thousand times; what am I nubuntu'ing here? Something fairly obvious? Is there a 'skip' button somewheres? 

Input appreciated, thanks in advance ye installation gurus.

---

### Post by shadowhacker on 2009-02-26
The largest continuous free space option won't work? It worked for me, but this was several months ago.

---

### Post by Aped on 2009-02-26
Hey! A response!

But this is what I see when I select that: 

[img]http://img187.imageshack.us/img187/6385/contiguous.png[/img]

It would be nice if the partitioner showed actual numbers in addition to percentages, maybe this is only 100% of the available space it's going to take? Hate to risk it, I patched the 'dozer and restored a lot of my stuff and downloaded crap and patched games... I feel screwing up here would give me a serious case of the kick-myself-in-the-rears. 

Weeell, if anyone has suggestions feel free to drop em in here! If I manually formatted the blank space as ext2/3, would the installer see that and let me install there without forcing me into these silly options?

If I *do* decide that I want to pre-format, and I'm obviously not sure about that yet, do I want to make it a primary partition? Think xp has one of those itself... and does ubuntu require a tiny swap partition? 

Again, much obliged sirs (and possibly ma'ams).

---

### Post by shadowhacker on 2009-02-26
No, you are correct, it will use the whole hard drive; go with the manual option. Make a new partition in the free space and format it ext3. That's weird that the continuous free space option would do that. The manual selection is quite intuitive though, and you should be able to figure it out. It will do exactly what it says it will. I hear you on doing it exactly right, when I first installed I was the same way, it would suck to lose hours and hours of work getting windows tuned in just right.

Under manual, set-up your ext3 partition and your swap partition in the free space, and mount / to ext3 and swap to swap. Also, I recommend making a 3rd partition and mounting /home to it for future re-installs or upgrades.

---

### Post by mcduck on 2009-02-26
Both "Guided, use the largest continuous free space" and "manual" require you to push the "Forward" button before you see the real results (or get to actually do the manual partitioning). Even if unsure, it's safe to continue as no changes are done immediately, you'll get a window with details about what's gong to be done and option to confirm the changes or return back to previous stages.

---

### Post by shadowhacker on 2009-02-26
Ah, thanks for clearing that up mcduck. I thought it was strange that it would do that. It's been so long since I've had to install Ubuntu, I'd forgotten exactly how it worked. That should say something, as I have the Windows installation procedure memorized. :rolleyes:

---

### Post by Aped on 2009-02-26
Thanks for the responses! McDuck, that's exactly what I was hoping to hear. I'll boldly hit that Forward button and pray for the best when I get home. 


For the record, though, it's not my FIRST linux install, just my first attempt at a dual boot :D

---

