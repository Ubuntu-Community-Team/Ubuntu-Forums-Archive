---
title: "Moving Ubuntu to a different partition"
date: 2008-11-10
forum: General Help
---

### Post by dave_didlydodo on 2008-11-10
I installed 8.04 some time ago, really as an experiment, to run alongside XP. It's now my main OS but the partition it's in is getting full. There is plenty of space on my HDD and I can create a much larger partition. But is there any way of moving my Ubuntu installation to the new partition, or would it just be easier to do a fresh install of 8.10 to the new partition and re-install my various apps and drivers etc?

---

### Post by dave_didlydodo on 2008-11-10
Surely someone can help me with this!

How can I move an Ubunti installation to another (larger) partition?

---

### Post by giuspen on 2008-11-10
> **dave_didlydodo said:**
> Surely someone can help me with this!

How can I move an Ubunti installation to another (larger) partition?

why don't u just resize the partitions instead than move in other partition?
in this case it's easy, do it with the live cd and system->administration->partition editor

---

### Post by Sam on 2008-11-10
It's a bit tricky, but doable. You need to boot from an other system (other linux partition or live cd), then copy all the root filesystem to some other partition, then redefine some references that pointed to first partition (eg: mbr, /boot/grub/menu.lst, /etc/fstab, I don't remember if there are other).

---

### Post by jimv on 2008-11-10
Listen to the wise man about resizing your partitions.  Just pop the live cd in and resize your partitions.  It's the best, safest way.

---

### Post by dave_didlydodo on 2008-11-12
Thanks guys. I'll try the partition re-sizing.:)

---

