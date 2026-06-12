---
title: "[SOLVED] Ubuntu won't boot after massive PC upgrade"
date: 2008-09-20
forum: General Help
---

### Post by xjgnsdof on 2008-09-20
I upgraded my motherboard, CPU, RAM, and video card today, and I can't boot into Ubuntu. The Ubuntu logo stays on the screen, telling me that it is loading, but never loading the OS.

I booted from a LiveCD and couldn't reinstall Ubuntu because the partition manager didn't recognize my hard drive partitions. My WinXP installation did, though, so I know the partitions are there.

Any advice is welcome. I really need to boot into Ubuntu again.

---

### Post by Dayne89 on 2008-09-20
an upgrade like this would make any o/s fail to boot. especially the motherboard. my advice is install again, repartitioning the space you want ubuntu to be. (if you have a separate /home partition you wont even lose settings or files)

---

### Post by xjgnsdof on 2008-09-20
That's the thing: I can't reinstall Ubuntu because the partition manager doesn't see any of my partitions. I did reinstall Windows since I last tried, however, so I'll give it another shot.

---

### Post by xjgnsdof on 2008-09-20
Also, when I run the LiveCD, sudo fdisk -l returns nothing.

---

### Post by xjgnsdof on 2008-09-20
up

---

### Post by xjgnsdof on 2008-09-20
I found the solution on another thread: [http://ubuntuforums.org/showthread.php?p=5827089#post5827089](http://ubuntuforums.org/showthread.php?p=5827089#post5827089)

When you get to the LiveCD menu screen, hit F6 and add "all_generic_ide" without the quotation marks at the end of the line.

Can someone explain why Ubuntu would fail to recognize hard drive partitions that were there?

---

