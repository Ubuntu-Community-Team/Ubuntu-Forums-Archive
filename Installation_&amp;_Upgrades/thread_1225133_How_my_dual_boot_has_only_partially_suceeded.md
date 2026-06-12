---
title: "How my dual boot has only partially suceeded"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by addisor on 2009-07-28
I've been using 8.10 64 on my desktop for a few years, so have reasonable grasp of terminal etc. My XP laptop (Toshiba Portege) finally got a dual boot makeover (sorry guys, still need XP for printing)

I followed the install procedure on the 9.04 i386 CD and asked it to do an alongside set up. This worked fine, both boot up. My problems are, in order of severity.

Update Manager states not enough space on / for files and i have constant permission problems. I actually suspect that jaunty installed on a small disk space and left nothing for extra's, help?

Firefox bookmarks wont stay, fwd/back arrows greyed out.

synaptic wont install anything

Any advice?

---

### Post by merlinus on 2009-07-28
```
df -h
```

will show disk usage.  If indeed you have run out of room on /, that is the source of your problems.

Here is an excellent guide about fixing the problem:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by addisor on 2009-07-28
thanks i'll report back

---

### Post by presence1960 on 2009-07-28
sounds like you probably made the mistake many make when choosing the side by side option: failing to specify how much space to give Ubuntu. The most common result of this is a root partition of 2.9 or 2.3 GB- hardly enough to update or save any files to.

---

### Post by addisor on 2009-07-28
That does appear to be the case, will that also solve the firefox issues?

---

### Post by presence1960 on 2009-07-28
> **addisor said:**
> That does appear to be the case, will that also solve the firefox issues?

I would reinstall. First as always back up any data you simply can not lose. Then make sure windows is defragged at least once or twice. When you install using the side by side method choose how much space to give Ubuntu by grabbing the end of the graphic shown and sliding the mouse to give it up to the amount of space you want for ubuntu.

Or prior to installing you can use the Ubuntu Live CD Partition Editor (gparted) or the Gparted Live Cd to create a partition or unallocated space  for Ubuntu by shrinking the Xp partition to create a new partition or unallocated space for Ubuntu. Then fire up the install process and install to that new partition or unallocated space. Either way will work.

---

### Post by addisor on 2009-07-28
all worked a treat, thanks guys

---

### Post by presence1960 on 2009-07-28
Glad you got it working. Enjoy Ubuntu!

---

