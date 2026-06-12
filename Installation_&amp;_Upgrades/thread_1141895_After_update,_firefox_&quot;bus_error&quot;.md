---
title: "After update, firefox &quot;bus error&quot;"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by rustyslacker on 2009-04-28
After running the latest batch of automatic updates (which included some firefox ones), Firefox fails to open at all. 

It was odd. I had the update running behind my browser, and when it said "please restart firefox" I had just clicked on something so it didn't load, and stopped firefox with an error. I closed it, and then the computer locked up and I rebooted it. 

So since that, Firefox refuses to open at all. I reinstalled it from Synaptic and apt-get, twice. I installed Epiphany and that doesn't start either. Running from terminal results in "bus error". 

Help D:

---

### Post by RT236 on 2009-04-28
> **rustyslacker said:**
> After running the latest batch of automatic updates (which included some firefox ones), Firefox fails to open at all. 

It was odd. I had the update running behind my browser, and when it said "please restart firefox" I had just clicked on something so it didn't load, and stopped firefox with an error. I closed it, and then the computer locked up and I rebooted it. 

So since that, Firefox refuses to open at all. I reinstalled it from Synaptic and apt-get, twice. I installed Epiphany and that doesn't start either. Running from terminal results in "bus error". 

Help D:

Same thing just happen here a few minutes ago.  I also just reloaded Firefox now from Synaptic and have similar errors as you.  I'm sending this from Wine running the Windows version of Firefox.  This is a very recent Firefox update for the Linux release, this evening it seems, as I checked Ubuntu updates earlier today and there were none for the Firefox Linux release.  I've been using Firefox Linux practically since the first release and I've never had this happen...

---

### Post by kostkon on 2009-04-28
Maybe the restart of Firefox didn't go well and its process is still running. Try giving this command in a terminal
```
pkill firefox
```
and then try to run Firefox again.

Hope that helps.

---

### Post by RT236 on 2009-04-29
> **kostkon said:**
> Maybe the restart of Firefox didn't go well and its process is still running. Try giving this command in a terminal
```
pkill firefox
```
and then try to run Firefox again.

Hope that helps.

Thanks, I should have thought of this, too long at PC today, getting flaky.  The prior release was still running, killed it...  rebooted too because of a lot of changes I did today with Ubuntu 9.04 (really nice release).  Then reloaded latest Firefox 3.0.10 from Synaptic (I had deleted it) and Firefox plus all extensions, bookmarks, etc. all came back.

---

### Post by coolnezz on 2009-07-26
wracked my brains for a few hours on this problem.  it happened after hard booting my computer, it was probably a damaged file system.
this solved it for me:

removing of xulrunner, nspluginwrapper and firefox and
re-installing fixed the problem.

---

