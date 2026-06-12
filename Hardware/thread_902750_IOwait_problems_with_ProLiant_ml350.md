---
title: "IOwait problems with ProLiant ml350"
date: 2008-08-27
forum: Hardware
---

### Post by esj on 2008-08-27
ubuntu 8.04
HP Proliant ml 350
E200i sata raid card

The problem is the I/O wait percentage increases during data transfer.  A simple rsync transfer will bring the percent I/O wait value up to the mid-40s and a little more stress causes the percentage to climb to upper 90% range.  All of the recorded fixes so far referred to upgrading the kernel but we are running the latest generic kernel.

Any suggestions?

---

