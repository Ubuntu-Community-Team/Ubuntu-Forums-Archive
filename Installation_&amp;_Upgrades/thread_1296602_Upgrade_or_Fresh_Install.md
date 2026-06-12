---
title: "Upgrade or Fresh Install?"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by PatrickBoyle on 2009-10-20
I've been using 9.10 beta for about a week now and just yesterday ran into a system crash that caused disk corruption.

I'm in a position now where I'm deciding whether to install 9.04 and set up everything to my liking, then upgrade to 9.10 in nine days, or simply use my Windows machine until 9.10 comes out and then do a fresh install. Are there any issues with upgrading between major versions?

Having been in the Windows world for many many years, my instinct is to shriek at the thought of performing an upgrade to the next major OS release. Is this not so for Ubuntu?

---

### Post by dhavalbbhatt on 2009-10-20
As a general rule, you should always perform a fresh install. In your case, I would say, wait 10 days before you install 9.10. Until then, you can always use 9.04 LiveCD for any other activities using Ubuntu!

---

### Post by Sef on 2009-10-21
In general, fresh installs have less problems than upgrades.  However, most people in either case, do not have any major problems.

---

### Post by PatrickBoyle on 2009-10-21
Thank you for the replies. I'm going to go ahead and wait.

---

### Post by cariboo on 2009-10-21
There are tools to deal with disk corruption, usually caused by a hard power down. If fsck doesn't run automatically on boot, you can boot from the Live CD and run fsck on your corrupted partition. Open an Applications-->Accessories-->Terminal and tpye:

```
fsck -a /dev/sdx
```

where /dev/sdx is the device label of the partition eg: /dev/sda1

---

### Post by emigrant on 2009-10-21
sorry if im going off topic,
having said that a fresh install is the best thing,
im wondering whether most of the members format the linux parition every 6 months?
because that makes the stability of linux unused.

---

