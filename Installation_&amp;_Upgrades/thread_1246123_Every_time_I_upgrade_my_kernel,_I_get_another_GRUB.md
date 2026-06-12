---
title: "Every time I upgrade my kernel, I get another GRUB entry - why?"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by spaceballl on 2009-08-21
Every time my kernel gets upgraded, I get yet another GRUB entry when my system boots. I'd really like to keep it simple... Ubuntu, Ubuntu Safe Mode, and Vista - how do I get rid of the old entries? And how do I stop Ubuntu from adding more and more?

---

### Post by donpedrodos on 2009-08-21
The most simple solution is just to [edit your 'menu.list']("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/").

After you cleaned up you 'menu.list, you also can remove the old kernel versions via synaptic.
Thats the way i work after a kernel update.

---

### Post by howefield on 2009-08-21
> **spaceballl said:**
> Every time my kernel gets upgraded, I get yet another GRUB entry when my system boots. I'd really like to keep it simple... Ubuntu, Ubuntu Safe Mode, and Vista - how do I get rid of the old entries? And how do I stop Ubuntu from adding more and more?

An option would be to install startupmanager using Synaptic Package Manager. Load it up and select the "Advance" tab and tell it how many kernels you want to keep on your boot menu. 

Reboot to see the magic all done...

---

### Post by Twittery on 2009-08-21
> **spaceballl said:**
> Every time my kernel gets upgraded, I get yet another GRUB entry when my system boots. I'd really like to keep it simple... Ubuntu, Ubuntu Safe Mode, and Vista - how do I get rid of the old entries? And how do I stop Ubuntu from adding more and more?

Well ubuntu has an habit of keeping old kernels even after updating it and some find this helpful because if they occur with some trouble with the new kernel they can boot with the old  . Easiest thing you could do id to remove old entries in /boot/grub/menu.lst  and delete the old kernel via [Synaptic]("http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/") .

---

