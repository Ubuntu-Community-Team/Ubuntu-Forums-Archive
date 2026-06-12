---
title: "mouse button bounce"
date: 2018-02-19
forum: Hardware
---

### Post by JKyleOKC on 2018-02-19
Within the last few weeks, my Logitech M510 mouse has developed an intermittent bounce in its buttons, so that an attempt to drag something becomes a double-click rather than a click-and-hold-while-moving. This is on 14.04 LTS kept fully updated, and I don't find any configuration setting that appears to address the problem. I've installed the solaar package, updated it from github since the copy in the official repository here is way out of date, but this problem appeared suddenly before my most recent update to solaar -- which I did in an effort to diagnose what's happening.

Any suggestions? I've tried using "xev" to determine how close in time the press and the unwanted release happen, but it's so intermittent that I've yet to catch it on a screen!

---

### Post by Autodave on 2018-02-19
Try another mouse.  I have several lying around here that have the same problem: some cheap ones and one rather good gaming mouse.

I have, on rare occasions, seen where a power supply can also cause the same issue.

Try another mouse: if that fixes it, bury old mouse. If it doesn't, try your mouse on another machine and see if it has that problem. If not, you may want to look at the power supply.

---

### Post by #&amp;thj^% on 2018-02-19
> **JKyleOKC said:**
> Within the last few weeks, my Logitech M510 mouse has developed an intermittent bounce in its buttons, so that an attempt to drag something becomes a double-click rather than a click-and-hold-while-moving. This is on 14.04 LTS kept fully updated, and I don't find any configuration setting that appears to address the problem. I've installed the solaar package, updated it from github since the copy in the official repository here is way out of date, but this problem appeared suddenly before my most recent update to solaar -- which I did in an effort to diagnose what's happening.

Any suggestions? I've tried using "xev" to determine how close in time the press and the unwanted release happen, but it's so intermittent that I've yet to catch it on a screen!

Sadly I have the same issue, but when I removed "solaar" problem gone!
It is a shame I really liked solaar. :(

---

### Post by JKyleOKC on 2018-02-19
> **Autodave said:**
> I have, on rare occasions, seen where a power supply can also cause the same issue.
It's a cordless unit, with two AA cells powering it. This prompted me to change out the cells to see if that might be the cause. It's only been a few minutes, not long enough to know for sure, but so far it hasn't bounced again.

Thanks!

EDIT: It's been 12 hours now, and no recurrence of the bounce, so I'm marking this thread solved. Thanks again for putting me on the right track; I would never have suspected the batteries!

---

### Post by JKyleOKC on 2018-02-22
Sorry to un-solve this one, but the problem resurfaced a day later, and it persists with yet another mouse. It shows up most consistently when playing Solitaire so that's how I'm testing possible solutions now. I suspect the xwindows pointer interface may have changed somehow in the most recent (past 60 days worth) of security updates, but it might be in the USB drivers for the Logitech cordless units. The other one I've tried was very old, pre-dating the unifying receivers -- it's the model that used a magnetic switch to turn off the mouse when the dongle was placed back on its underside! Since both mice show the same symptoms, though, and do have different Logitech receivers, I suspect the problem to be even deeper in the stack of procedures that go between the mouse and the screen!

---

### Post by cybrsaylr on 2018-02-22
Had a similar erratic mouse movement problem with wireless Logitech M185 and M310 mice. Both are optical mice. Got no help posting here awhile back. Talked to a geek buddy at Best Buy who said to make sure the desktop it's used on is clean. Did that and it worked fine for awhile. Then the erratic cursor movement returned. Geek buddy asked if I use a mouse pad? I said no, thinking they were no longer needed with optical mice. He said try using a mouse pad again. I did and that seems to have corrected my jumpy mouse problem. Mouse movement is stable and solid again.

---

### Post by JKyleOKC on 2018-05-30
Here it's four months later and the problem is back worse than ever. It's consistent across three different mice, one a brand new M510, one a much older logitech cordless optical (the model with the magnetic switch to turn it off when the dongle was stuck to its bottom), and the third a wired HP with USB connector. Also present on both 14.04 and 16.04 systems, which tends to rule out a corrupted driver. I'm not using solaar on this box, either. The multiple clicks are beginning to make the system almost unusable!

---

### Post by Autodave on 2018-05-30
I would be looking at your power supply: especially the 5V part of it.

If you have anything else plugged into a USB port, try disconnecting all of them and see what happens. It could even be a USB keyboard: try playing solitaire w/o the keyboard connected.

---

### Post by JKyleOKC on 2018-05-30
Well, your mention of power made me look at the hub into which I've plugged all three test mice, and since it's on the end of a maximum-length cable I thought that might be at least part of the problem. I moved the receiver for the M510, which is the current one, to a front-panel USB port and am testing. There's still a bit of bounce, but it seems to be somewhat reduced.

Since the problem appears only on this one box, which has been in almost 24/7 service for quite a few years and has already outlived one power supply, it's quite possible that the current power supply is getting weak -- or even that the mobo hardware for USB processing could be getting flaky! Thanks for triggering some new thoughts!

The hub in question includes provision for connecting an external 5V wall-wart, but I've not yet connected one. That will be another test, as soon as I find such a transformer in my junk closet.

---

