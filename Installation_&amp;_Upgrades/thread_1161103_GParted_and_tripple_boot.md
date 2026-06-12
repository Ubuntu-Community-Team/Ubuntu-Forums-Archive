---
title: "GParted and tripple boot"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by linuxguru1 on 2009-05-16
Hi,

I recently installed a second windows XP partition. It gave me the problem of not being able to start up ubuntu, but that got fixed. Now however, I have another problem. 

I assumed the windowspartition I want to be able to boot should have the "boot"flag and the other one should have the "hidden" flag. It worked fine like that for quite a while but yesterday that system somehow failed. The windowspartition I wanted to boot got stuck on booting. I figured it was still on "hidden" and went with the other partition.
Now however, I need to boot the partition that doesn't want to start up. But when I set the flags correctly and rebooted, the windowpartition in question failed again. I took another look in GParted and saw that the other windowspartition stole the bootflag from the partition that doesn't want to start up.
I set the flags correctly again and rebooted. Same problem. Same explaination.

Could anyone help me out with this? Is this one of the windowspartitions freaking out or am I missing something?

Thanks.

---

