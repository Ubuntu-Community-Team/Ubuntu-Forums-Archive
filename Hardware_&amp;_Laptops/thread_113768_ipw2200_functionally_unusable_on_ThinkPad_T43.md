---
title: "ipw2200 functionally unusable on ThinkPad T43"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by DrSturgeon on 2006-01-07
I feel stupid asking the umpteenth ipw2200 question on this forum, but I can't find an answer in anything else.  When I'm using the wireless connection on my t43, the system will hard freeze frequently--sometimes the caps lock light flashes, sometimes not.

It's only a problem if the interface is actually up.  Sometimes it will freeze as soon as I bring it up (ifup eth1), and sometimes it'll work for a while, and then freeze.  Never works for more than an hour at a time.

This is with both the version of the driver that comes with Ubuntu, and the version in luca_linux's famous WPA howto.  Both suffer from the problem.  I tried the newest version of the driver, but had some trouble getting it compiled.

Yes, the proper firmware is in the proper place.

Any ideas?  Thanks.

--Dan M.

---

### Post by DrSturgeon on 2006-01-07
Sorry to be persistent, but Windows is pissing me off.

Anybody?

--Dan

---

### Post by escape on 2007-08-14
I'm actually having this problem as well on my T43. I've tested with 2.6.21-r2 and 2.6.22-r2, using ipw2200-1.2.2, ieee80211-1.2.18, and ipw2200-fw-3.0. Everything was running fine until I recompiled my kernel for some CD-ROM related options; now when I try to modprobe ipw2200 I get a hard lock and the caps lock key flashes. No solution yet...

---

### Post by K.Mandla on 2007-08-14
Flashing caps lock lights are sometimes associated with kernel panics, I believe. If you're working with a recompiled kernel, it's possible you tweaked something that interferes with the hardware configuration. Can you re-examine your kernel setup? Is there a chance you omitted or added something that would conflict with the module and kernel?

P.S.: Is this your bug?

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114329](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114329)

---

