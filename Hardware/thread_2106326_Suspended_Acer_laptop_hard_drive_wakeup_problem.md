---
title: "Suspended Acer laptop hard drive wakeup problem"
date: 2013-01-18
forum: Hardware
---

### Post by JanciR on 2013-01-18
Hello,
When I suspend (s2ram) my Acer 8930 laptop under both Ubuntu 10.4  and 12.4 same problem appears. Laptop can hibernate (s2disk) well, but suspend (s2ram) is not working. After suspend it freezes on wakeup and when I press Ctrl+Alt+F1 this text is being periodically printed out:

[4480.58016] ata1: irq_stat 0x00000040, connection status changed
[4505.402689] ata1: SError {DevExch}

[4523.58053] ata1: irq_stat 0x00000040, connection status changed
[4521.415321] ata1: SError {DevExch}

[4535.58853] ata2: irq_stat 0x00000040, connection status changed
[4585.458621] ata2: SError {DevExch}
...

and so on, only the number in Square brackets [] changes.

I tried to install uswsusp and hibernate packages from synaptic but no change,,
I also tried most of options of s2ram with no success.

Thanx

---

### Post by ahallubuntu on 2013-01-18
Suspend to RAM doesn't use the hard drive.  Hibernate does save the memory image to disk (to your swap space), though, but you say that works.  I suspect the suspend problem has nothing to do with your hard drive.

There was a bug filed related to suspend for this laptop way back in Ubuntu 9.10:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362512)

Sometimes these bugs are never fixed, unfortunately.

---

### Post by Toz on 2013-01-18
Do you get these messages before suspend as well? If so, it might indicate a hardware problem of some sort. I've seen messages like these before when there is a bad cable. Maybe try to reseat the hard drive?

And btw, welcome to the forums.

---

### Post by JanciR on 2013-01-27
Window suspend works well so it is definitely not a hardware problem Toz.
So I reopened the bug in the link you posted ahallubuntu is it all I can do for now?

---

