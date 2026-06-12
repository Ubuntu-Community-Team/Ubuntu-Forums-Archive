---
title: "how long to resize partition?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by lactosedave on 2009-04-21
I've been resizing the partition on my laptop using freed space for about 20 minutes and it still says 0% and I hear no working sounds coming from the hard drive.  Should I be concerned?  I really don't want to stop now. I feel like that could be bad.

---

### Post by Mark Phelps on 2009-04-21
Resizing can take HOURS -- because it really does it twice -- once in a trial mode, and then a second time for real.

If you're using GParted (in LiveCD boot) or running the GNome Partition Editor, you should have a panel that will allow you to expand the actions to at least see if it's doing anything.

---

### Post by lactosedave on 2009-04-21
The screen went black about 15 minutes ago, is that a bad sign....

---

### Post by lactosedave on 2009-04-21
scratch that. Resize failed.  Aborted.  Any advice?

---

### Post by Keithhed on 2009-04-21
Did you get any failure message?

---

### Post by lactosedave on 2009-04-21
it said essentially what was in my lost post.  I can't remember the exact wording.

---

### Post by lisati on 2009-04-21
As has been pointed out, resizing can take hours: on one of my laptops (which has a 160Gb HDD) it took something like 5 hours.

Did you take note of the error message(s) that popped up, so we can help troubleshoot?

EDIT: Oh. Just spotted the previous post. We must have been typing at the same time.

---

### Post by lactosedave on 2009-04-21
It doesn't want to let me leave Vista in tact now. The use freed space option has mysteriously vanished. Any thoughts?

---

### Post by upchucky on 2009-04-21
on a couple of occasions I have had gparted fail during partition tasks, i then switched to partedit. it picked up off where gparted quit.

---

### Post by Mark Phelps on 2009-04-22
Would strongly advise against using GParted to resize Vista OS partition.  Have seen numerous posts where this has resulted in corruption to the Vista OS -- which is generally fixable by booting from a Vista DVD and doing Startup Repair.

Suggest using the Vista Disk Management tool (yeah, I know how poor it is).  See the following links for some things you need to consider:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

If you MUST use GParted to shrink it, make sure that the "Round to nearest Cylinder" option is disabled.  Also, download and burn the latest GParted LiveCD from distrowatch.com and use that instead of the Ubuntu LiveCD.

---

### Post by redspider on 2009-04-22
if there are certain parts that cant be moved use perfectdisk.  there is a trial version. i had to use that cause vista and ubuntu couldn't move some files at the begining of the harddrive.

---

### Post by redspider on 2009-04-22
if it shows as no more free space to shrink defragmenting usualy helps

---

### Post by Godly on 2009-04-22
Hours.....can seem like forever!

---

