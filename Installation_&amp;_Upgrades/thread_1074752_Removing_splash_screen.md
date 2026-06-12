---
title: "Removing splash screen"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by ChakaZulu on 2009-02-19
I finally got Ubuntu 8.04 installed on my Compaq laptop, duel booting with Vista. The problem is that when it tries loading up it sits at the splash screen for a long time then exits to a shell and ends up at the initramfs prompt. I read a few threads that said removing the splash screen might help but if I can't get past the initramfs part, how can I edit it? I tried hitting F6 when it's booting but that did nothing. Is there something I can type at the prompt to get it to keep loading or to change the splash screen option? I'm so close to being able to use this software....

---

### Post by ChakaZulu on 2009-02-19
Ok so I found this link which enabled me to get past the splash screen so I could see what was going on:
[http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/)

This is what I get on the screen after it tries to boot:

check root=bootarg cat /proc/cmdline
or missing modules, devices:cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/e34(bunch of numbers here) does not exist. Dropping to shell!

Busybox...etc....

(initramfs)

---

### Post by ChakaZulu on 2009-02-20
^ bump

---

