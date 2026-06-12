---
title: "Initramfs busybox errors occurring"
date: 2021-05-28
forum: Hardware
---

### Post by uacnt83982803 on 2021-05-28
I have had 2 occasions where upon a reboot, I see a bunch of "read-only filesystem" errors fly by on the screen, and then the system restarts and presents a console window with an initramfs busybox shell (for lack of a better word).

I run fsck on the bad device and let it repair everything, and it then restarts and operates fine.

This problem *seems* to occur after the system has suspended itself several times (i.e. from inactivity).  

Are these errors indicative of a failing hard drive?  Are there other disk diagnostic tools that I should run to check things out?

Using Ubuntu 20.04LTS on an Acer laptop, about 4 years old.

Thanks.

---

### Post by guiverc on 2021-05-28
If problems keep occurring it can be a sign of hardware issues.. but even good hardware will misbehave if fed poor power.

To check your disk health, use it's SMART capability - [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)  (you can also check drive health via GUI tools too).

If issues only occur after an event.. that's a clue as to where to look, but with only two occasions you don't yet have a pattern, in my opinion (is your power line good? no nearby heavy power-drawing devices like fridge/freeze, microwave etc that happened to turn on at the exact same time?)

---

### Post by uacnt83982803 on 2021-05-28
Hi, thanks for the advice.  The laptop is powered by a UPS so the incoming power should be good.  There's no large loads on that circuit.

I will try the SMART tools and see what shows up.  Thanks!

---

### Post by uacnt83982803 on 2021-06-15
So I am still having this problem.  The partition that gets messed up varies between /dev/sda1 and /dev/mapper/ubuntu/--vg-root.

Just ran the extended SMART test.  The assessment in every case is "OK".

It only exhibits this problem when I log back in (I generally lock it when leaving it) or resume after Suspend.  I can use it for hours on end without issue.  But if I leave it (locked or suspended), often this problem happens.

I don't know what to try next.  Any suggestions?  Here is the SMART diagnostics results table:

---

