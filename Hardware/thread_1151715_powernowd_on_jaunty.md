---
title: "powernowd on jaunty?"
date: 2009-05-07
forum: Hardware
---

### Post by niallporter on 2009-05-07
Hi all,

I notice that the powernowd is no longer installed by default (i'm on 9.04 x64).  Checking /proc/cpuinfo reveals that all 8 cores in my machine are running at 1.3GHz (rated max of 2.5GHz).  I'm finding that it doesn't matter how hard I push the CPUs they never clock back up to full speed.

In the past it was easy, disable the powernowd (or cpuspeed on Red Hat) and that disabled the down-clocking of idle cores.  How can I disable this behaviour in Jaunty?

Thanks in advance,
Niall

---

### Post by kpkeerthi on 2009-05-07
Look in System -> Administration -> Services

---

### Post by niallporter on 2009-05-07
> **kpkeerthi said:**
> Look in System -> Administration -> Services

I did.  It's not there (or anything else which purports to manage CPU frequency scaling).  What do you suggest I look for?

---

### Post by stefangr1 on 2009-05-07
Maybe you should check out this thread:

[http://ubuntuforums.org/showthread.php?t=21370](http://ubuntuforums.org/showthread.php?t=21370)

May I ask what type of hardware you have (with 8 cores...)? I think the values in /proc/cpuinfo are not always correct, and it is possible that cpu scaling on your system is in fact working as it should. Do you notice underperformance of your system?

You can benchmark your system by measuring the time it takes to perform a certain action, then kill powernowd:

sudo pkill powernowd

and then measure again how long it takes to perform the same action. If you notice a difference, you know something is indeed malfunctioning.

---

### Post by niallporter on 2009-05-07
> **stefangr1 said:**
> Maybe you should check out this thread:

[http://ubuntuforums.org/showthread.php?t=21370](http://ubuntuforums.org/showthread.php?t=21370)

May I ask what type of hardware you have (with 8 cores...)? I think the values in /proc/cpuinfo are not always correct, and it is possible that cpu scaling on your system is in fact working as it should. Do you notice underperformance of your system?

I'm on my computer at work, HP xw9400.  2x Quad-Core AMD Opteron 2360SE, 16GB.  With all due respect, I don't want to get into a discussion as to whether or not I *should* disable CPU scaling, I asked *how* to do so.  For what it's worth, it's not such an issue for me because I tend not to run high-end apps (unless you count 4 or 5 concurrent VMWare virtual machines as high-end apps) but my users do.  What I've found in the past is that as I said in my OP, the scaling clocks chips down, but never back up.

> **stefangr1 said:**
> You can benchmark your system by measuring the time it takes to perform a certain action, then kill powernowd:

sudo pkill powernowd

and then measure again how long it takes to perform the same action. If you notice a difference, you know something is indeed malfunctioning.

I can't kill powernowd if it's not installed.  It isn't, yet all 8 cores are running at 1.3GHz instead of the full 2.5GHz.  Is CPU scaling built into the kernel now or something like that?

---

### Post by stefangr1 on 2009-05-07
CPU scaling is build in to the kernel. Apparently powernowd is no longer used in Jaunty.

Did you already read this thread:

[http://ubuntuforums.org/showthread.php?t=1111609&page=2](http://ubuntuforums.org/showthread.php?t=1111609&page=2)

You can now use rcconf to change the scaling behaviour.

PS: I did understand that you wanted to get rid of the scaling alltogether, but considering that your attempts to do so failed, it could be useful to find out whether the cpu scaling fails, or just the monitoring. As the latter does not affact performance.

---

### Post by niallporter on 2009-05-13
> **stefangr1 said:**
> CPU scaling is build in to the kernel. Apparently powernowd is no longer used in Jaunty.

Did you already read this thread:

[http://ubuntuforums.org/showthread.php?t=1111609&page=2](http://ubuntuforums.org/showthread.php?t=1111609&page=2)

You can now use rcconf to change the scaling behaviour.

PS: I did understand that you wanted to get rid of the scaling alltogether, but considering that your attempts to do so failed, it could be useful to find out whether the cpu scaling fails, or just the monitoring. As the latter does not affact performance.

Thanks for the response.  I installed rcconf and can see the ondemand thing which I gather now handles the CPU scaling.

However, I took your suggestion and installed stress, I had it hammer all 8 cores at once and checked - it seems the CPU scaling in Ubuntu now works correctly.  Each of the cores jumped to the full 2.5GHz when under stress and dropped back to 1.3GHz when quiet so I'll leave it be.

The fact that all previous versions of Ubuntu (or any Linux for that matter) that I've run on this machine have failed to scale CPU speed back up made me think that it must be an intrinsic limitation in the CPUs rather than the software, I guess I stand corrected.

Thanks all for the help and advice :)

Niall

PS. Do I mark this thread as SOLVED myself or does an admin do it?

---

