---
title: "Need help installing Ubuntu in IBM T30 while preserving hidden partition"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by shellhrs on 2007-02-08
When my friend saw me using an old IBM TP 600e running Fluxbuntu, he was hooked. He asked to me to install Fluxbuntu (or Ubuntu) in his system, an IBM TP T30.

I had some concern though, because AFAIK T30 had a hidden partition for recovery from system crash. I've used it before, and Windows XP was installed automatically.

My friend wanted to hidden partition so he could reinstall XP if necessary. The existing XP can be deleted if necessary, but not the hidden partition -- and the one-touch recovery system.

Can anyone give me advice for this?

---

### Post by mocoloco on 2007-02-08
I use a T42 and it had the recovery partition but I decided to trash it to have more space, so I'm not speaking from firsthand experience but my understanding is you should be able to just install as usual, just manually edit the partition table and create an extended partition to setup logical partitions for your Ubuntu home, root, and swap (or whichever partitions you want to have).  As long as you don't touch the recovery partition I think everything should be fine.
Can anyone who kept their recovery partition intact confirm this?

---

