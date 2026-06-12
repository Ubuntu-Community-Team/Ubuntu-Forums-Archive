---
title: "How to enable the Mute LED ?"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by yotamkr on 2006-06-14
Its not the first time that someone asks this question but somehow i still didnt find a good answer...
I have an HP ze2000 laptop and there is a Mute button which works, but the orange LED dosent light while the computer is muted (as in the Windows XP)....
any ideas??? thanks

---

### Post by yotamkr on 2006-06-15
bump

---

### Post by yotamkr on 2006-06-18
bump

---

### Post by muganor on 2007-12-20
Look at : [https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/124331](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/124331)

It shows how to enable the mute led on two laptops, with different sound modules.

You may execute "lsmod | grep snd" to figure what is your sound module and patch the "options ... ac97_quirk=7" line with the appropriate module.

---

