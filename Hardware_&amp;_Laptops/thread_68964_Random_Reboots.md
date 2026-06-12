---
title: "Random Reboots"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by koan on 2005-09-24
Hi.

I have Hoary installed, and have been running it for a few months.  Over the past few weeks however, it has started rebooting randomly.

Nothing has changed from a hardware perspective, but I suspect it is a hardware issue.  Running memtest shows nothing, and there are no clues in syslog or messages.  It seems to be most likely to happen when there is sustained disk activity, such as reading a large file, or large quantity of files.

I am pretty new to linux, and especially diagnosing a fault like this.

Can anyone tell me if there are other logs or tests I can run that will help me isolate this problem?

Thanks,

koan

---

### Post by kosmic on 2005-09-25
if it only happens when you are using the disk, the it can only be 2 things, 1º the Hard drive have bad sectors in it, or 2, you have a faulty ram, but if you already run the memtest program, and it didn't report anything, the probably the problem is the disk.

---

### Post by Benzima on 2005-09-27
I had a very similar problem a couple years ago although I was running Widows 98 back then. After beating my brains out and swapping out numerous parts, all problems immediatly dissapeared after I put new RAM in.

---

