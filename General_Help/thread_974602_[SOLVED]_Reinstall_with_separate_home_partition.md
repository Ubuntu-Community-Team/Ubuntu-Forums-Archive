---
title: "[SOLVED] Reinstall with separate /home partition"
date: 2008-11-07
forum: General Help
---

### Post by bilijoe on 2008-11-07
Over the last couple of months, I've been having more and more funny little glitches occur.  I'm running 8.04.1.  I've also experienced extremely sluggish performance, on a more and more frequent basis.  I noticed recently that /etc/fstab is all screwed up--seems to be describing a different system altogether.  I don't even know how the thing can run with completely invalid info in fstab.  Today, the system froze hard for the second time. (Oh my God!  Did I just admit to having a Linux system freeze up?  Well, what can i say--it happened--froze hard enough that I had to pull the plug to free it up.)

In any case, rather than try to figure out these several problems, and fix fstab, I thought I'd just reinstall the system.  Last time I did an install, I set up a separate partition for /home.  Does that mean I can reinstall the system, without having all my preferences, settings, bookmarks, etc., overwritten?  Can I just do a straightforward install, and then reconnect the separate partition to /home?  (I know I did that before, but how do I tell the system to mount that partition as /home, every time it starts?)

Is there any good reason NOT to do a reinstall, since I seem to have several problems at once?

---

### Post by aged hippy on 2008-11-07
If i may suggest, rather than pulling the plug, try *<Ctrl><Alt><PrintScreen>* held down all at once, then one at a time while still holding down *<Ctrl><Alt>,* holding each letter for a couple of seconds: ***r s e i u b***

Maybe someone else will help with the installation question. :)

---

### Post by Idefix82 on 2008-11-07
When you do a clean install, simply choose the manual install option, choose the existing /home partition and tell the installer to use it and to mount it as /home. Don't forget to untick the "format" check box for this partition or your data will be lost. Create all the other partitions you need afresh or use the existing ones but format them and you are done.

---

### Post by bilijoe on 2008-11-08
> **aged hippy said:**
> If i may suggest, rather than pulling the plug, try *<Ctrl><Alt><PrintScreen>* held down all at once, then one at a time while still holding down *<Ctrl><Alt>,* holding each letter for a couple of seconds: ***r s e i u b***  I've not heard of this before.  What is the intended result?

---

### Post by Idefix82 on 2008-11-08
This should answer your question:
[http://ubuntuforums.org/showthread.php?t=617349]("http://ubuntuforums.org/showthread.php?t=617349")

---

### Post by aged hippy on 2008-11-08
> **bilijoe said:**
> I've not heard of this before.  What is the intended result?

It re-boots the system. :)

***Edited to add:***
It is much less likely to lead to corruption of data.

---

