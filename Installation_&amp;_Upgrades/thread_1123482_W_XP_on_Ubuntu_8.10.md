---
title: "W XP on Ubuntu 8.10?"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by jazzline on 2009-04-12
Hello,
I'm trying to install windows XP on Ubuntu 8.10. I would like to work it so that I can choose during the boot whether I use Windows or Linux. Dual boot, I believe it's called. I have about three hundred questions, I start with these:
I have Linux installed on drive sda, I have a brand new drive, sdb, which I intend to use (or at least half of it) for windows. Is that possible at all?
And how should "grub.conf" look like? I understand that BIOS is written so that it goes first on first drive sector 1 (hd0,0). Can I tell there that in case of windows jump to hd1,0??? 
In case windows overwrites my Linux boot, how can I get my Linux back?
jazzline ](*,)

---

### Post by hyper_ch on 2009-04-12
windows usually needs to be on the first partition of the first drive... so you'd need to switch the drives around. Or unplug the ubuntu drive, install windows on the other drive and then plug in the ubuntu drive again. Then you just need to (manually) add win xp to grub.

That's probably the simplest way.

---

### Post by jazzline on 2009-04-13
> **hyper_ch said:**
> windows usually needs to be on the first partition of the first drive... so you'd need to switch the drives around. Or unplug the ubuntu drive, install windows on the other drive and then plug in the ubuntu drive again. Then you just need to (manually) add win xp to grub.

That's probably the simplest way.

Thanks, a lot (million thanks) the simplest is often also the best.
jazzline

---

