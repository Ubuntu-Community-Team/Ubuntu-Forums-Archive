---
title: "Lost System Prefs of Removable Drives!"
date: 2009-04-28
forum: Hardware
---

### Post by yarko on 2009-04-28
Hi -

I've been running 9.04 RC last week, all weekend (fun!) - updates came in once in a while;  I installed things, tested things, built things, had general fun.

I left my work windows in the laptop, and booted from usb drive - 4 days, all great.

Here's what I know - my usb drives were auto-detected (numerous times), and even the partitions of my internal 320G drive were showing up on my "Places" menu - they were'nt automounted, but they would "ask" to mount when I tried to get at them from my places - sweet.

Today, after work, I boot from my usb again - no auto-detect of the "other" usb drive;  no presence of any of those other drives on the "Places" pull down.  Of course I tried the docs ([https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)) and looked around a bit.   There's also no menu item System->Preferences->Removable Drives and Media   any more.

Now, I _have_ been installing a lot of things (building Python, testing on several versions).....

Any clues of what to look for, where to start?

I checked out udevadm, it runs, did an info-dump of the data, or what the udev daemon thinks it sees, and it all looks ok.

One thing I noticed - I'd mounted a desktop image from one of these "other drives" - but I fixed that (copied the image to my home, set it, rebooted).

Thanks for any pointers.

Regards,
Yarko

---

### Post by yarko on 2009-05-09
Ok - no one has bitten on this one...

So here goes:

I think in all the installs (and eagerness to boot ubuntu only - leave "others behind permanently"...  I grabbed all my favorite development libraries...

I think what botched my system (and is itself not in great shape) is the GTK developers libs.

So I "clonezilla"'d my botched (320G) drive to a new 500G.  Let's see how this goes...

Now - I can try to figure out what got stepped on, and why updates, etc. don't see it, find it, or fix it...  or I can try to re-install (ubuntu & user partitions distinct)  and go from there.

I spotted someone else talking about "backup before you do upgrades / installs...

which begs the question:

What do people do for backup / rollback?   hg or git the entire unix space to a separate drive / partition?  rsync? (at least that's a one shot roll-back).

Itchy fingers,
Yarko

---

