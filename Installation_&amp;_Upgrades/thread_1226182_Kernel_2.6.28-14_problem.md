---
title: "Kernel 2.6.28-14 problem?"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by jaysonfw on 2009-07-29
Hi all,
After installing upgrades on 9.04 today, I get a grub error that says 
Unsupported or Invalid executable
Press any key

Pressing a key takes me to a list of kernels. 2.6.28-13-generic works, but 2.6.28-14 causes the grub error. Any ideas how I can fix this?

Thanks
(Advanced Noob)

---

### Post by slumbergod on 2009-07-29
During the updates my system completely locked up. After rebooting and finishing off the updates, then rebooting again, I was startled to hear the system beep had come back. I thought "yippee!" they have finally fixed all the regressions and maybe the physical volume control will be working again (it has been dead since I moved to Jaunty). But no, the update seems to have completely killed all sound on my system.

Another fantastic set of updates (sarcasm).

[edit] rebooting to kernel 2.6.30 seems to have fixed the problems. Whatever they've done to 2.6.28-14 it's now poisonous.
Kernal PPA: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Xubuntu 9.04 + ext3 + alsa

---

### Post by victorsmonster on 2009-07-29
I'm having a similar problem with the updates. I'm using an old Dell Latitude D610. Everything was working great until last night's updates, and now I get jumbled video when I boot. 

[LIST]
[*]Booting from the 9.04 CD is fine, so I know it's the updates causing the problem.
[*]Booting from an older kernel produces the same jumbled video
[*]"Try to auto repair graphic problems" (xfix) doesn't fix the problem
[/LIST]
At least I was able to recover my data to an external hard drive using the 9.04 Live CD.

Any suggestions?

Edit: I know there are two possible video cards in the Latitude D610. I don't know if mine is the Intel or ATI variant.

---

### Post by jaysonfw on 2009-07-29
My issue was related to kernel 2.6.28-14 playing nice with ext4 filesystem. It was resolved by following the instructions on this link:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331)

Let me know if this fixes your issue as well

Jayson

---

### Post by Biermacht on 2009-07-29
tnx...solved my problem!!!

I use ext4 ...now grub loads with the 2.6.28.14 and 2.6.30.3 kernels

---

