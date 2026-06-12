---
title: "Grub2 10 seconds hangup"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by potam on 2009-09-13
Hello all,

I have upgraded grub legacy on my Jaunty box to grub2. Grub2 loads just fine, but when I hit enter on the kernel line to boot, I got an empty screen with blinking cursor for about 10 seconds, before "Loading please wait" appears, and the boot splash shows up.

I have only one harddisk, with one root and one swap partitions, root is ext3. I attached the generated grub.cfg file. No matter if I take out the UUID pass from /etc/default/grub, or use a grub2 splash image or not, 10 seconds hangup remains. How should I fix this?

---

### Post by potam on 2009-09-19
Up

---

### Post by potam on 2009-09-20
Additional information: It is clear now, that the "quite" kernel option caused the delay. Without that I got instant (but ugly) boot. So it seems to be a bug, maybe fixed in later releases.

---

### Post by potam on 2009-11-01
Problem no longer exists in Karmic.

---

