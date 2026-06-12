---
title: "[SOLVED] Odd bug"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by kaurman on 2008-02-13
Hi!

I'd like to hear your opinions on a [bug in launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/155142/") 

The main points of it are here:

I am using Gutsy and I've noticed a strange problem:
> 
When using the 2.6.22-14 kernel the hdd is making a strange high pitch sound similar to some kind of beeping. I suspect that the head is constantly moving even when the computer is idle and this can not be good. When I boot up with 2.6.20-16-generic the problem is gone.

and

> 
The combination which causes the beeping is: enabled speedsteping + 2.6.22-14-generic kernel. If I disable the speedsteping, generic kernel works fine.

2.6.22-14-386 kernel works fine and it doesn't seem to care whether speedsteping is enabled or disabled. This is a bit odd though as Fr Ch said that 386 kernel didn't help.

The only conclusion I can make about this bug is, that it has something to do with CPU cores as I have a dual core and 386 uses only one of the cores.

Any ideas?

Thanks in Advance,

Kaur

---

### Post by kaurman on 2008-03-18
Solved. Check the bug report.

Kaur

---

