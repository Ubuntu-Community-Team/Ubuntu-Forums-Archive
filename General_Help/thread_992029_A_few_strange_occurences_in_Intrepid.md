---
title: "A few strange occurences in Intrepid"
date: 2008-11-24
forum: General Help
---

### Post by aaronLund on 2008-11-24
Hi all.  

I'm on a HP xw4100 desktop running Ubuntu Studio 8.10.

Couple of things that have been bothering me and I figured I should ask someone about them:

1) I have an nvidia video card (GeForce Fx 5200) so I cannot enable the desktop 3d effects, it seems.  Perhaps there's been a workaround?

2) When I boot up, my login screen is huge.  I can just barely see the "name" and "password" input box but I can enough to sign in.  Once I'm signed in everything is fine it's just that the sign-in screen is so big, it's like I'm seeing the upper right hand corner of it.  Not too sure about that one....

3)  Is there some sort of log somewhere that will tell me why my computer seems like it has been shut down after a night?  It's odd because the lights on the computer are on (this includes mouse and keyboard) but the monitor reports "no signal".  Then I have to do a hard restart, etc.

4)  Not too sure why but sometimes--after a restart-- I'll have to edit my xorg.conf from "nvidia" to just "nv" or I can't get in to X.  This doesn't happen all the time but often enough that it's a pain.

I'm wondering if all of my problems are stemming from this nvidia video card.

Thanks for any advice.

---

### Post by CatKiller on 2008-11-24
> **aaronLund said:**
> I'm wondering if all of my problems are stemming from this nvidia video card.

Almost all, I suspect.

> 3)  Is there some sort of log somewhere that will tell me why my computer seems like it has been shut down after a night?  It's odd because the lights on the computer are on (this includes mouse and keyboard) but the monitor reports "no signal".  Then I have to do a hard restart, etc.

That just sounds like the monitor has gone to sleep to me - or at least, it's tried to. You might have a setting on the monitor to let it go to sleep with [DPMS]("http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling") so that the monitor properly turns off, or you could set the monitor to never turn off with System -> Preferences -> Power Management. You should be able to wake the display up by moving the mouse or pressing a button, the same as you would with a screensaver.

---

### Post by aaronLund on 2008-11-24
> **CatKiller said:**
> You should be able to wake the display up by moving the mouse or pressing a button, the same as you would with a screensaver.

Yeah, that's what I thought too.

However, none of this seems to "wake" the thing up.  (Only a hard restart, obviously).  That's why I was looking for some sort of log where I can figure out exactly what's going on.

Thanks for the reply!

---

### Post by CatKiller on 2008-11-26
It's possible that one of the screensavers has taken down X, leaving you without mouse or keyboard. That used to happen to me with Compiz quite some time ago, but hasn't happened for some time. In principle, you could still SSH into the machine from another and restart X if this is the case.

Or possibly the machine was trying to hibernate and failed.

I'm not sure which logs you'd look in to check either scenario though, I'm afraid.

---

