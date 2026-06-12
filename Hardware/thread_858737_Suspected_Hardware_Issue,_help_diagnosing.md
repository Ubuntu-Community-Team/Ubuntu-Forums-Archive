---
title: "Suspected Hardware Issue, help diagnosing"
date: 2008-07-13
forum: Hardware
---

### Post by Chris Murphy on 2008-07-13
Hi,

I've been having an occasional issue with my computer, its very sporatic.  What happens is my computer will freeze, either when idle, or when performing a task.  I(nor a linux savvy friend) have not been able to trace the problem back to anything software related, and the system log hasn't recorded anything consistent over the last 4 freezes(all today, previously to this the computer has been fine for about 3 weeks, and previously to that it was freezing about once a week).  The problem has persisted through Linux Mint, and Hardy Kubuntu and Ubuntu distro's being installed.

Pressing the reset button does not allow the computer to restart, previously the start up was displaying what appeared to be ip addresses when it would hang, it would run through many very quickly, and if left to do this for about half an hour it would eventually stop and become unresponsive.  Now the startup screen runs through several succesfully started processes, hangs at "Starting Basic Networking" for about 10 seconds then displays "Killed" on the line below, and becoming unresponsive.

The power switch on the supply must be turned off for ~10 seconds then the computer will restart, or if the computer is booted off the live CD, shut down and restarted it will boot from the hard drive.  This leads me to believe something is being kept alive in memory that is causing the problem.

When the computer does restart, it makes displays a message about an orphaned inode, but it passes too quickly to write down all the numbers it gives, the system log recorded an orphaned inode being deleted after some(but not all) of the successful restarts, always inode 263561, however this is a different number than given during start up.

Please help, the computers hardware is still under warranty, and I'm at the end of my ability to further diagnose this problem, which has gotten much worse today for no discernible reason.

---

### Post by cyclobs on 2008-07-14
it maybe a cpu problem,

but try to run a memtest (from the ubuntu cd)

---

### Post by Sef on 2008-07-14
> it maybe a cpu problem,

but try to run a memtest (from the ubuntu cd)

Memtest is for your ram.  It needs to run about 8 hours.

---

