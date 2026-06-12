---
title: "Boot hangs with ipw3945 switch off"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by makro on 2006-11-10
I often have this problem:

if I boot with ipw3945 switch off, the pc hangs and sometimes shows "BUG!: soft lockup on CPU#0" message

I'm sure this is something to ipw3945 or restricted-modules related.

Any help?

---

### Post by benhall on 2006-11-10
I can't offer any advice, but I've noticed the same problem on my laptop. It usually seems to happen at the fsck stage.

---

### Post by makro on 2006-11-10
fsck stage isn't involved... simply something happens after that stage... something about ipw3945..

---

### Post by antraxx on 2006-11-11
> **makro said:**
> I often have this problem:

if I boot with ipw3945 switch off, the pc hangs and sometimes shows "BUG!: soft lockup on CPU#0" message

I'm sure this is something to ipw3945 or restricted-modules related.

Any help?

Exactly same problem at my Thinkpad R60.I'm trying to solve this problem by  dissabling ipw3945 module in /etc/modprobe.d/blacklist. But this is not solution.

Has anyone any idea, hoe to solve this problem.

---

### Post by lingnoi on 2006-11-29
I have this problem too.

I made a bug report beforehand here:
[http://bugs.launchpad.net/distros/ubuntu/+source/nvidia-kernel-common/+bug/71029](http://bugs.launchpad.net/distros/ubuntu/+source/nvidia-kernel-common/+bug/71029)

---

