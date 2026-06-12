---
title: "my pen drive isn't mounting for 2nd time..."
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by crixtiano on 2006-01-12
Hi, 

I'm using Ubuntu version 5.10 (breezy).

I have a pendrive (Corsair Pendrive) and I'm having a problem with Ubuntu.

The first time I connect the pendrive in PC, by USB port, it's work fine and I don't have any problems.

But, if I unmount the pendrive and if I mount it again, Ubuntu some times mount the pendrive very slow. Sometime, I wait, wait, wait and the pendrive isn't mounting.

Please is it a bug? What to do to finish this problem?

10ks

Cristiano

---

### Post by tim15856 on 2006-01-12
I saw this post [http://ubuntuforums.org/showthread.php?t=90643&referrerid=40811](http://ubuntuforums.org/showthread.php?t=90643&referrerid=40811) and I'm going to try it to fix my USB flash drive problem. Mine worked fine for a couple days. Then I inserted a different flash drive. That one worked fine too, but afterwards, neither drive will mount. In fact, the computer stalls when I insert it. Maybe it'll help you.

---

### Post by mhl978 on 2006-01-12
When I encounter this problem, running "sudo /etc/init.d/hotplug restart" from terminal will generally force recognition of any flash device.  Best of luck.

---

