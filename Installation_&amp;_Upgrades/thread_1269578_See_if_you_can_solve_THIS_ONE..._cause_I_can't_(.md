---
title: "See if you can solve THIS ONE... cause I can't :("
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by daevski on 2009-09-18
This is a decently long story, but I will try to make it short. **Esscially**, I had an easy install from disc, ran the system for a whlie, something went wrong and now the boot disc does nothing after the boot screen... :

I get a copy of **Ubuntu 9.04** and go to install on a newer pc with win7 already on it. I boot from disc, install ubuntu on free space and everything is fine. I install avant, screelets, nvidia prompts me to install drivers; all that fun stuff...... all is well. I reboot several times, edit little things, and then, after one reboot, ubuntu decides not to boot past the loading screen. Maybe I did something wrong. [long story short] I run through diagnostics and can't seem to understand what is up.

Everything seems normal up to this point, but after trying to 
1. burn a new install CD (incase the one I had got effed-up)
2. clearing the partition with win7 (incase something on it was causing this)
3. Mem test in windows and from Ubuntu disc
4. Hard drive tests in windows...
and everything else I could think of to get back to square 1, **the boot disc will not get past the loading screen!**

This makes no sense to me because it worked perfect on my PC the first time, and after several restarts.

Any thoughts?

*I did use the same CD and monitors (yup 2 of them: **17 inch CRT with VGA** and a **37" tv on DVI**) to install ubuntu and run it for about a week now on a different box. -- It's just this one PC that is driving me nuts.

---

### Post by drs305 on 2009-09-18
Did you do a "side by side" install with Windows? If so, make sure you have space on your / partition:
```
df -h
```

There is a chance that it installed on a 2.5GB partition, and that soon after the install it ran out of space. If you don't understand the results of the command post them here.

---

### Post by daevski on 2009-09-18
Well, I created a chunk of 45gigs on the 200gig hdd -- I think it was "free space", but reguardless it installed correctly and I ran the OS for like 4 hours...

then after going back to square 1, as listed above, the install stopped after the boot screen, exactly like the OS had after it was running for hours.


Aside from swapping out another video card, I'm completely baffled. I'm going to try that later today or tomorrow and I will update this thread with the outcome.

---

### Post by Chronon on 2009-09-18
What partitioning scheme did you use for Ubuntu?  

It sounds a little bit like you're saying that the Live CD won't even boot for you.
> boot disc will not get past the loading screen!

I had a drive go bad on me once and I could only boot from a Live CD if it wasn't attached.  This doesn't sound like the problem in your case, though.  Still, it might be worth seeing if the Live CD will boot properly if you remove the drive first.  At least it gives a way to see if the drive (or any of its contents) has anything to do with what's causing hangups for the Live CD.

---

### Post by daevski on 2009-09-21
That's actually not a bad idea. I just had a motherboard that wouldn't post correctly because of a dud HDD -- strangest thing I'd ever seen (except maybe this post's issue...)

I will keep you updated after I try a bunch of hardware swapping today.

---

### Post by Joshua Lückers on 2009-09-21
What about using a LiveUSB?

---

### Post by daevski on 2009-09-21
Another good idea. I will try that next!

---

### Post by daevski on 2009-09-21
> **daevski said:**
> That's actually not a bad idea. I just had a motherboard that wouldn't post correctly because of a dud HDD -- strangest thing I'd ever seen (except maybe this post's issue...)

**I will keep you updated after I try a bunch of hardware swapping today.**

Okay so I just tried a bunch of stuff:

1. Unplug all SATA cables from HDD (left cables connected to MoBo -- no fix.
2. Swap Video card for a different one -- no fix.
-->(swaped video card back in)
3. Unplug SATA cables from MoBo -- FIX!

Plugged all hard drives back in and all seems to be running fine.

Conclution: SOMETIMES SH!T JUST NEEDS TO BE RE-SEEDED... ?:-\

---

