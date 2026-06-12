---
title: "Partition Editing -- REALLY kind of important!"
date: 2008-08-11
forum: General Help
---

### Post by VivaLaEva on 2008-08-11
EDIT: NEW QUESTION!
Having accepted the fact that I've royally boned myself [again ><] in the partition/OS department, and realizing that a fresh install is inevitable, I was wondering if there's a way to save/back up all of my Ubuntu configs, from appearance to apps to every little update that's happened between the LiveCD and now...is there a way to do all of that so I can just install Ubuntu exactly the same way as I ruined it?

ORIGINAL STORY:
Ok, well.
I've been playing around with partitions for a good week or two, installing new secondary operating systems and screwing up my primary, y'know, standard stuff.

Well just when I thought I got it all figured out, and my Ubuntu partition was safe and I could just mess around with the 10 gig partition I made for testing out new things...I tried to write a new flag to said 10 gig partition.

And, well, as it turns out, I somehow managed to screw up THE ENTIRE THING.
All of my partitions -- my 10 gig, my main, my linux swap...all now 149-odd gigs of "unallocated" space.

But...I'm still using Ubuntu.  Even though gParted claims that I've gone and done and screwed up everything, I'm still typing and using my main partition, which apparently no longer exists.

My question to you-all is --- what am I supposed to do now? I'm afraid that if I touch ANYthing, the whole system'll come crashing down.  And while it's not a huge deal, and I won't actually lose anything important [hoo-rah for HDDs!!], my LiveCD is a good 2 months old or so and there have been over 300 updates...and it's a pain in the *** :(

Sorry for the essay, thanks for the time!!

---

### Post by Yuki_Nagato on 2008-08-11
Did you use GParted while inside of Ubuntu?  Or did you use the seperate GParted CD and then boot up Ubuntu afterwards?

You can delete your entire Ubuntu system while running it and it will at times still continue to run just fine until you restart it.

As for a direct solution, I am at a loss.

---

### Post by tuxxy on 2008-08-11
Fresh install on new partitions if you not going to mess it up again :lolflag:

---

### Post by ntu on 2008-08-11
> Well just when I thought I got it all figured out, and my Ubuntu partition was safe and I could just mess around with the 10 gig partition I made for testing out new things...I tried to write a new flag to said 10 gig partition.

Could you not just revert the boot flag back to where it was originally?

---

### Post by VivaLaEva on 2008-08-12
> **Yuki_Nagato said:**
> Did you use GParted while inside of Ubuntu?  Or did you use the seperate GParted CD and then boot up Ubuntu afterwards?

You can delete your entire Ubuntu system while running it and it will at times still continue to run just fine until you restart it.

As for a direct solution, I am at a loss.

I used GParted while inside Ubuntu.
And that's what I was kind of wondering -- things'll be good..'til I have to restard..and then I've got a completely clean, unformatted HDD...damn, I'll be updating all night ><

> **ntu said:**
> Could you not just revert the boot flag back to where it was originally?

I think it was one of those once-you're-done-you're-done type deals.

And, I guess, if that's the case..I may as well get to rebooting soz as I can re-set up my laptop...damn ><

DOUBLEEDIT
Ignore last edit. Wishful thinking. *sigh*

---

### Post by VivaLaEva on 2008-08-12
Ok, well, I've accepted the fact that I'll be re-installing [I'm trying to put it off as much as possible, I'll probably wait until this weekend when I don't have work].

MY NEW QUESTION IS:
Is there any way to SAVE my current Ubuntu configs? Like, save the appearance, save the apps installed/removed, save the 3rd-party sources..save EVERYTHING, in the exact state it's in now?

---

### Post by rokytnji on 2008-08-12
MY NEW QUESTION IS:
Is there any way to SAVE my current Ubuntu configs? Like, save the appearance, save the apps installed/removed, save the 3rd-party sources..save EVERYTHING, in the exact state it's in now?


[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

Its in synaptic package manager.

---

