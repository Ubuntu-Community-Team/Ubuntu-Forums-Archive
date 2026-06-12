---
title: "Dual booting Ubuntu and Slackware"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by tonyW303 on 2009-05-25
I have Ubuntu 8.10 and only Ubuntu 8.10. No other OSes or partitions (except for SWAP). I would like to also put Slackware on my laptop. I do not have GRUB or anything like that... At least i dont think so... Anyway, what do I need to do to get Slackware and Ubuntu dual-booted?
Thanks in advance!

---

### Post by andrew.46 on 2009-05-25
Hi tony,

> **tonyW303 said:**
> I have Ubuntu 8.10 and only Ubuntu 8.10. No other OSes or partitions (except for SWAP). I would like to also put Slackware on my laptop. I do not have GRUB or anything like that... At least i dont think so... Anyway, what do I need to do to get Slackware and Ubuntu dual-booted?

Well I suspect that you actually *do* have [grub]("http://en.wikipedia.org/wiki/GNU_GRUB") installed as it is more than likely that it boots your existing system :-). There are many different ways to do this but I would personally suggest:

[LIST=1]
[*]Use gparted to create a partition for slackware.
[*]Install slackware to this partition and install lilo to the root of the partition *not* to the mbr
[*]Chainload your slackware installation from grub on the mbr
[/LIST]

This way you get to experience the simplicity and power of lilo as well as the power of slackware :-). Swap can be shared.

There are so many variations of this and no doubt others will suggest several more options. My own variation of this is to run slackware as a primary distro and run Hardy, Intrepid, Jaunty and Windows XP on Virtualbox and virtualisation is another thing to consider.

All the best with this,

Andrew

---

