---
title: "Kernel issue after waking up from suspend with Karmic"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Piscium on 2009-11-03
Suspend always worked fine with Jaunty. I have updated to Karmic, and now, every time I wake up from suspend I have a notification of a kernel issue. 

This issue does not seem to have any obvious effects, though perhaps there could be some subtle consequences like memory corruption. I have still not used it enough to come to a conclusion. 

I wonder if anybody else had this issue.

I am attaching a screenshot from apport.

---

### Post by Piscium on 2009-11-03
Update:

I downloaded an update with Update Manager and the issue is fixed (or more precisely, pushed under the carpet!). ;)

I think that this fix could also help other people that are getting a lot of Apport notifications.

Here is the relevant bug that was fixed:
[https://bugs.launchpad.net/ubuntu/+source/kerneloops/+bug/471137]("https://bugs.launchpad.net/ubuntu/+source/kerneloops/+bug/471137")

---

