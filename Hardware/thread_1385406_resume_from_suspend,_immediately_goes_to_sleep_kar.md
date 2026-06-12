---
title: "resume from suspend, immediately goes to sleep karmic"
date: 2010-01-19
forum: Hardware
---

### Post by cenzorrll on 2010-01-19
Hi, I've been having an issue with suspending since moving to Karmic.  It's not a huge problem, just an irritation.

occasionally, when I wake up from suspend the computer wakes up for a few seconds then immediately goes back to sleep.  I've looked through log files to see if anything comes up, but I didn't see anything that really stuck out besides a "finished suspend" or something like that.

one thing that i find a bit strange is that if can input my password before it goes to sleep, it'll wake up again without asking for a password.

any ideas?  anyone else have this?

I could swear it's a Power Management issue rather than the actual process of suspending, but I'm not too familiar with the internals of it.

(I'm using an HP TX2500 if it helps)

---

### Post by cenzorrll on 2010-01-20
bump

---

### Post by cenzorrll on 2010-01-21
okay, some progress on discovering the problem.  it happens when i suspend while the ac cord is plugged in and wake up on battery (close lid with ac in, open lid with ac out)

i figure if no one posts after 24 hours then i'll submit a bug report.

---

### Post by cenzorrll on 2010-01-22
HA HA, what luck. update manager just came up with this for gnome-power-manager:

Version 2.28.1-0ubuntu1.1: 

  * debian/patches/09-fix-double-suspend.patch:
    + Manually check lid status in gpm_manager_client_changed_cb. Fixes
      double-suspend bug (LP: #425411)

edit: yarp, that did it, at the moment it's one of the ubuntu proposed updates. marking this thread as solved

---

