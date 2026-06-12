---
title: "Problem with wubi installing from windows 7"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by o0-leo on 2009-11-06
From time to time I'm checking up with new ubuntu releases.
I mostly do this with wubi, and didn't have any problem with it till now..
I'm using windows 7, and when i try to clean-install ubuntu 9.10 with wubi, after the first restart, i get an error massege that says wubildr cann't be found on each partition it tries to find it, Though i can see the wubildr.mbr and wubildr files in the c: drive, under my windows installation.

The hda0-0 search says "no wubildr", the hda0-1 search says "0" and other searches prompted "null"...

I've searched the net and only found unanswered topics.. and solved ones which doesn't relate to clean installs.

Please help me, I really want to try ubuntu 9.10. :)

Thanks, leo.

---

### Post by Mark Phelps on 2009-11-06
Seen lots of posts with problems with the combination of Windows 7 and Ubuntu 9.10 -- and no solutions to date.

The Wubi guide doesn't mention support for any MS Windows OS newer than Vista although some folks have reported success with Windows 7 and Ubuntu 9.04.

---

### Post by o0-leo on 2009-11-07
The number of windows 7 users is Increasing rapidly, so it's quite a problem.
There is no workaround?

---

### Post by Mark Phelps on 2009-11-07
> **o0-leo said:**
> The number of windows 7 users is Increasing rapidly, so it's quite a problem.
There is no workaround?

Not at this time.  The problem seem to be a combination of the new partitioning default scheme in Windows 7 coupled with the new GRUB2 in Ubuntu 9.10.

MS, obviously, has no incentive at all to do anything about the Windows 7 side of the problem.

Remains to be see if the Wubi developers abd GRUB developers are going to "fix" the Ubuntu/GRUB2 side of the problem.

---

### Post by o0-leo on 2009-11-08
The question is, are they aware of it?

---

### Post by ckop64 on 2009-11-08
I don't really trust Wubi, so i usually try new distros with virtualbox.
I have a combination of Win7 and Ubuntu 9.10, with a normal installation of both, and they work fine for me. :)

---

### Post by o0-leo on 2009-11-08
ok, I get that some people don't like wubi, but i really like it...
So.. as I said.. are the Wubi developers aware of the problem?

If not, how can I report?

---

