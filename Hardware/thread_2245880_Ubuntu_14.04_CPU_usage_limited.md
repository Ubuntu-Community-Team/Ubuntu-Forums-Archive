---
title: "Ubuntu 14.04 CPU usage limited"
date: 2014-09-26
forum: Hardware
---

### Post by arvliet2 on 2014-09-26
I run an Ubuntu 14.04 instance on a multi-threaded single CPU.  

Running top shows all 8 cores, but even under heavy load, the aggregate cpu usage never rises much above 1/8th of the possible load or roughly 100% of a single core.  For instance, Thunderbird and Firefox may both be listed with 25% and 50% CPU usage while other processes make up the rest of the equivalent of "100%" usage of a single core.  

I've checked process to cpu affinity - that seems to be OK.  The kernel is SMP enabled.  I've been working on this for several weeks and not come up with anything significant.  

I have not yet tested with a live disk, but I'm expecting that should be fine.  I'll test and update, but in the mean time,  short of a full re-install *cringe*, I'm not sure what else to do.

Thoughts?  Ideas?

---

### Post by slickymaster on 2014-09-26
*Moved from to the *[s]General Help[/s] **Hardware*** sub-forum*

---

### Post by weatherman2 on 2014-09-26
What are the contents of the file /proc/cpuinfo ?  Are four processors (0 to 3) listed there or just one?

(FYI, there are only four cores - each one with two threads, presumably.)

If there are four cores...if you want to tax all four cores, open a terminal window and type this (same thing four times):

```

dd if=/dev/zero | gzip -9 > /dev/null &
dd if=/dev/zero | gzip -9 > /dev/null &
dd if=/dev/zero | gzip -9 > /dev/null &
dd if=/dev/zero | gzip -9 > /dev/null &

```

[I]Don't close this terminal window yet.

[/I]That should put all four cores into action (and probably slow the computer to a crawl).  Now type:

```
top
```

You should see four gzip processes at the top - using how much CPU?

[I]When you are finished, hit Ctrl-c . To kill the gzip processes, type:

[/I]```

killall dd

```

---

### Post by arvliet2 on 2014-09-26
I actually started 8 instances of the command.  Went into top, and the system is indeed showing that each thread is using some 80% of CPU.  Oh, and then I started a youtube video just to check.  Only had  very slight lag.

You see, that is /not/ what happens when i run anything started graphically through the GUI.  Most often, I end up with a few processes (firefox and thunderbird are the major culprits which cause high load) which when all the running processes are added together, they just don't add up to the ~ 800% cpu load we just confirmed.  The processes never go above 100 - which I expect because they're only a single thread.  But when multiple processes are hammering the CPU, the /total/ usage between all active threads doesn't add to more than about 100% CPU usage.

Clear as mud?

---

### Post by weatherman2 on 2014-09-26
Sounds completely normal.  A quad core CPU with two threads on each core is far more than a normal desktop needs.   Many processes don't use 100% of a core.  Even if you had only a single core/single thread, it would be typical to see all processes adding up to less than 100%.  gzip, though, is a highly CPU-intensive process which is why it takes so much of the load.

It sounds like you are worried that your computer is slowing down because processes are not using all of the CPU, but those gzips show that everything is working normally.

---

### Post by arvliet2 on 2014-09-26
I just tried with 8 instances of the command running under 8 instances of xterm.  The system wound up to 800% CPU usage and continued to purr along nicely.

---

### Post by arvliet2 on 2014-09-26
Normally I would agree, but your not catching that the CPU usage of Thunderbird, under load like when I force an indexing of several hundred thousand emails, in combination with the load of Firefox with a run-away plugin always seems to add up to under 100% CPU when, if I'm correct, they should be using as much CPU as they can get hold of.  If Firefox was running on its own CPU, it should have ~100%, not a floating 25%.  Thunderbird should have its own CPU too with near 100% usage, and the other apps would in theory shift around to the other cores as required, but they don't.  

Everything seems to always hang around 100% usage of a single core - even when some of those apps are under major load.

---

### Post by weatherman2 on 2014-09-26
Again, Firefox and Thunderbird may not use 100% of a core, and if you had only a single core, you still might see total usage adding up to under 100%.  Thunderbird for one is probably more I/O limited than CPU limited - i.e. limited by access to files than to CPU scheduling.  If Thunderbird is waiting for email messages to load, it probably isn't using much CPU at all.

You seem to believe that any process that is actively running will use 100% of a core, so two processes running should use 200%, etc.  That's simply not the case unless the process *needs* that much CPU time (or can get it, if it needs it).   CPU use isn't the only constraint on a process.

---

