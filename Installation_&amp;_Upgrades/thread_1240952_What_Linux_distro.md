---
title: "What Linux distro?"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by fela on 2009-08-15
I'm trying to choose a Linux distro for my mother (who doesn't have the best of technical skills, just wants a system that works). Ubuntu suited her very well (practically no tech support needed :)), but it runs more than a bit slow on the computer that I'm gonna install it on. I'd like something that's fast and lightweight, but as easy to use as Ubuntu. Any ideas? I'm thinking right now of Ubuntu with openbox or XFCE, but I'm wondering if there's anything else I might be missing out on.

It doesn't matter if there's the odd problem that's fixable with a bit of techy knowledge, I know /etc like the back of my hand so I can help her with that sort of thing.

Thanks :)

---

### Post by Anzan on 2009-08-15
No, I think those will work well.

I use Fluxbox, so I'll plug it here.

You could also try CrunchBang or LXDE, both of which use OpenBox..

There will be a 9.10 Lubuntu using LXDE.

---

### Post by Whiffle on 2009-08-15
What are the specs of the system we're talking about?

---

### Post by fela on 2009-08-15
> **Whiffle said:**
> What are the specs of the system we're talking about?

It's an old Dell optiplex. It has a 2.8GHz hyperthreading pentium 4 (not particularly good but does the job), and a very bad intel integrated graphics card that seemed to not work at all on Ubuntu 8.10. It ran incredibly slow and I suspect it was a fault on this part. The system has 512MB RAM so I don't want anything like KDE on it.

> **Anzan said:**
> No, I think those will work well.

I use Fluxbox, so I'll plug it here.

You could also try CrunchBang or LXDE, both of which use OpenBox..

There will be a 9.10 Lubuntu using LXDE.

Okay. Fluxbox - isn't really what my mum wants. She needs something that's easy to use and where she kind of knows where everything is (coming from OSX). Thanks anyway.

I've never actually tried crunchbang. I thought LXDE was a desktop environment in itself? If so - I tried LXDE once on my ubuntu server but only over FreeNX and VNC, so I don't know what that would be like. Worth a try I suppose.

About 9.10 - it isn't stable yet but I could give it a try once it is. I'd prefer something that never crashes though.

I think I'm gonna try Ubuntu with LXDE. It seems to work similarly to GNOME but lighter on resources.

---

### Post by Whiffle on 2009-08-15
Hmm.  That is similar to what I'm running ubuntu on right now and its really pretty snappy, except I have a slower processor, a similar graphics card, and 4 times the RAM.  So, I think RAM is your issue, in which case any desktop environment that uses less of it will run better than vanilla Ubuntu.  That said, a RAM upgrade is never a bad idea.  But LXDE looks like a good idea too, and cheaper.

---

### Post by Anzan on 2009-08-15
LXDE's default is kind of Win95 but I'm sure she'll like it. It's very fast.

And, yes, stay away from 9.10 for now (unless you want to test, of course).

---

### Post by fela on 2009-08-15
> **Whiffle said:**
> Hmm.  That is similar to what I'm running ubuntu on right now and its really pretty snappy, except I have a slower processor, a similar graphics card, and 4 times the RAM.  So, I think RAM is your issue, in which case any desktop environment that uses less of it will run better than vanilla Ubuntu.  That said, a RAM upgrade is never a bad idea.  But LXDE looks like a good idea too, and cheaper.

Sure it could be RAM usage, I've noticed that later versions of Ubuntu seem to be using more and more RAM. I could run 7.04 really well on a P4 with 256 megs, but when I installed 8.10 on a better P4 with 512 meg, it doesn't seem to run well at all. I think it's the graphics though, I still think that because the one with 256MB had a much better GPU (not good, but much better: geforce FX5200).

I think openbox or LXDE on ubuntu would solve that though. I'll see what I can do.

> **Anzan said:**
> LXDE's default is kind of Win95 but I'm sure she'll like it. It's very fast.

And, yes, stay away from 9.10 for now (unless you want to test, of course).

I can change the win95 stuff, theming isn't important right now. As you said, I don't think she'd care anyway!

---

### Post by Whiffle on 2009-08-15
I've found that running Compiz with some pretty basic settings (no effects, just desktop transitions and scale and such) actually makes it feel snappier, and I'm using a Intel 915 GMA on here, plugged into a monitor at 1280x1024.

Still no comparision to my desktop, which is out of commission at the moment, which blows my mind because it finishes doing everything before I know what I want it to do...its THAT fast.  To me anyway...

---

### Post by fela on 2009-08-15
> **Whiffle said:**
> I've found that running Compiz with some pretty basic settings (no effects, just desktop transitions and scale and such) actually makes it feel snappier, and I'm using a Intel 915 GMA on here, plugged into a monitor at 1280x1024.

Still no comparision to my desktop, which is out of commission at the moment, which blows my mind because it finishes doing everything before I know what I want it to do...its THAT fast.  To me anyway...

This graphics chip was made before Compiz even existed. :lolflag:

BTW, what are the specs of your desktop? You can see mine in my sig.

---

### Post by Whiffle on 2009-08-15
C2D E8400, 4 GB DDR3 (currently being RMA'd...and backordered, yay!), 9800GTX+, Gigabyte GA-EP45-UD3LR 


Going from a 1.6GHz pentium 4 to that was quite a jump.  For now I'm using my T43, which is 1.86GHz pentium M, and it does well enough.  

And, I just installed LXDE, and so far I like it very much, its snappier than gnome.

---

### Post by fela on 2009-08-15
> **Whiffle said:**
> C2D E8400, 4 GB DDR3 (currently being RMA'd...and backordered, yay!), 9800GTX+, Gigabyte GA-EP45-UD3LR 


Going from a 1.6GHz pentium 4 to that was quite a jump.  For now I'm using my T43, which is 1.86GHz pentium M, and it does well enough.  

And, I just installed LXDE, and so far I like it very much, its snappier than gnome.

OK your desktop has a quite alot faster CPU, bit faster RAM but with higher latencies (same amount), and a bit better GPU. So overall it's quite alot better :lolflag:

But just wait till I upgrade to a Phenom II 940 Black edition quad core...two thirds the speed of a Core i7 920 I hear :P.

PS my desktop is snappy as ever even when compiling the Linux kernel! That's what I'm doing right now anyway. Almost finished...

---

### Post by Whiffle on 2009-08-15
Haha.  Yeah, I buy a new computer on average every 7 years, and generally don't upgrade it much in between, so this should last me for a while.  I'm not much of a gamer (but I loves me some half life 2 or left4dead), so that helps alot.   I'm actually debating buying a second monitor right now, since I'm going to be working from home soon, and it would help alot.

---

### Post by fela on 2009-08-15
> **Whiffle said:**
> Haha.  Yeah, I buy a new computer on average every 7 years, and generally don't upgrade it much in between, so this should last me for a while.  I'm not much of a gamer (but I loves me some half life 2 or left4dead), so that helps alot.   I'm actually debating buying a second monitor right now, since I'm going to be working from home soon, and it would help alot.

I so want a second monitor. I feel so cramped with a single 19 inch widescreen at 1440x900, LOL. Actually, I do.

---

### Post by Whiffle on 2009-08-15
Back in engineering school, we had dual 20" monitors at 1600x1200 hooked up to some of the machines with Nvidia quattro's on intel pentium D's runnning Fedora/XP.  That was heaven.  Everything was quick, and there was SO much space to work with.  Assignment on one side, work on the other, and a big comfy chair.  It really made certain assignments go much more smoothly.

---

