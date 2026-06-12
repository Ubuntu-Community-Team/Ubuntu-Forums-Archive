---
title: "After a power outage"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by nophix on 2005-08-18
The power went down (because of my neighbour, but that's another stupid story) yesterday and I've been running fsck on my ext3-partition. The / is fine where ubuntu is installed (3GB ext3), but my /home (77GB ext3) seems to have some errors and I must run ext3.fsck manually (couldn't run it with -p). The error on boot says "UNEXPECTED INCONSISTENCY", the usual one I guess. 

So I have been running fsck for 12 hours now, it asked a couple questions for some files on the first hour but I can't remember what questions now, something about "clone". I just answered yes. I can't even go back to it with shift+pageup anymore to check that again sorry.

My questions is, is this procedure gonna take days to fix or should I just give up? Is there something more I can do or should I just leave it? Is it safe to cancel the fsck? I've never experienced this procedure to be this long even though I've had the same problems before but with other hardware.

My computer is Duron 700, 384 RAM and a Maxtor harddrive.


P.S. Yes, I do have backups, although it's a week old but I still want to fix this for future experience. And should I maybe use another fs next time, like reiserfs? I have a lot of small files on my hdd.

---

### Post by nocturn on 2005-08-18
If it is going to get it fixed, it should take maybe 30 minutes tops, not hours or days.

So, I'm afraid something is really wrong.

I can recommend Reiser for this type of thing, I have had it for years now on several machines and not one problem.

---

### Post by nophix on 2005-08-18
The fsck-procedure is still asking questions. I came home about an hour ago and checked it out. It's asking for some files if I want to "Clone duplicate/bad blocks<y>" them. What does this mean exactly? Is it doing a copy of the files and putting it in lost+found? I don't have too much space left for that. :) 
Or is it deleting the original files on the way?

19 hours now... My patience is incredible.

---

