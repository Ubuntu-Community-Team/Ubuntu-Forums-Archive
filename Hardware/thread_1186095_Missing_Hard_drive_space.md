---
title: "Missing Hard drive space"
date: 2009-06-13
forum: Hardware
---

### Post by phantom3113 on 2009-06-13
I appear to have lost about 10 Gb of my harddrive. I have my harddrive partitioned to / and /home, 9.4 Gb for /, and (initially) 217 Gb for /home. A few weeks ago, I was trying to resize them to give 10 Gb from /home to /, but about 5 min. in changed my mind and canceled the operation. I didn't lose any data or anything, but the HDD space monitor screenlet now shows 9.4 Gb for /, and 207 Gb for /home. What happened to the 10 Gb, and can I get it back without having to reinstall anything (again)?

---

### Post by anystupidname on 2009-06-13
I'm not sure what partitioning utility you were using, but it sounds like it might have messed with your partition boundaries and not completed the operation. Obviously, aborting that type of operation halfway through is always a bad idea...

I can make some suggestions but I hope you have backups...

You could try testdisk and see if it finds and/or fixes the problem.

Baobab or filelight may or may not show you graphically where the space has gone...

---

### Post by iponeverything on 2009-06-13
It probably just got left as unallocated space.

If the hole is adjacent to the partition you want to expand it should be fairly easy to grow the partition in to that space.

---

### Post by phantom3113 on 2009-06-13
I was using GParted on the Jackalope 9.04 LiveCD. It makes sense for it to end up as empty, unused HDD space since I never lost anything. I'll try and give it a looking-at when I get the chance to and see if GParted shows any unused space

---

