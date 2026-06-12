---
title: "hard drive size support"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by dannyliu on 2006-02-13
Hi guys,

Like to share this exprience with you guys. Any comment is welcome.

I have a dell 4550 machine with XP. I added another hard drive to it and try installing Ubuntu. I succeeded the first time and found some bugs on ubuntu.
Then I reinstalled Ubuntu and failed several times. Finally, I figured out it was 
related to the partition size allocated to Ubuntu. The new drive is 250GB west digital. If I use the whole drive for Ubuntu, the grub loader cannot boot ubuntu
after installation. If use part of the drive, say 100GB, it works. It is wierd cause I could use the whole drive for ubuntu the first time.

Regards,
Dan

---

### Post by dannyliu on 2006-02-13
From delll comunity, one post indicates that 48-addressing is required to support
partition greater than 137GB. And XP sp1 and sp2 will fix it.

Don't know if there is a fix patch from ubuntu.

---

