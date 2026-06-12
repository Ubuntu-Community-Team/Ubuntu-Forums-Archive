---
title: "Lost Power During Automatic Upgrade"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by tadthebuilder on 2009-04-26
I was upgrading my computer to the newest edition of Ubuntu when I lost power to the device, thus shutting it down. It had already downloaded everything and was in the process of installing everything.
When I got power back I attempted to boot my computer.
It is a laptop, but it has no battery so it shut off when the power shut off
When I rebooted my computer it booted like normal, and even had the bar that slides over as it boots. When that was full it went to a black screen with text on it
At the bottom of this screen it says Checking Battery state....
/dev/sda:
setting advanced power management level to Oxfe (254)
after about ten or fifteen minutes of this it said [ok] on the other side
then:
stopping anac(h)ronistic cron anacron
then after a bit
starting anac(h)ronistic cron anacron
then 
stopping anac(h)ronistic cron anacron

It has stayed this way for a while now im leaving it on to see if it ever progressess.
I realize that I may have to install from a CD but Im hoping I do not have to
I have alot of data that is only on that computer and I do not back up, because Im am stupid.
Anyway any idea or advice or help?

---

### Post by PeEllAvaj on 2009-04-26
Have you tried booting from the recovery partition and running "fix broken packages"?  Even if the install was totally lost, you could still use the live cd to resize your partition. You could do this so you don't lose any of your data when you reinstall. After the reinstall you should have two partitions and you could just copy the files you want (/home/) from the bad install to the good one.

Hope this helps!

---

### Post by MedellinManDem on 2009-05-30
> **PeEllAvaj said:**
> Have you tried booting from the recovery partition and running "fix broken packages"?  Even if the install was totally lost, you could still use the live cd to resize your partition. You could do this so you don't lose any of your data when you reinstall. After the reinstall you should have two partitions and you could just copy the files you want (/home/) from the bad install to the good one.

Hope this helps!

I have the same problem as the OP, except I didn't wait around to see if it changed.

The "Fix Broken Packages" option didn't work...does anything else work?

---

### Post by kruegger on 2009-05-30
You may try testdisk. It is a simple but powerful tool for partitioning, fixing mbr, exploring current partitions...
It needs a little patience to read the tutorial but it is worth your while.
[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") can be obtained from any Ubuntu working repository.

---

