---
title: "Dual boot Ubuntu 8.04/Vista Partition Quandries"
date: 2008-08-03
forum: General Help
---

### Post by Meetloaf13 on 2008-08-03
Short story:

I installed Ubuntu HH 8.04 on my lappy that had Vista on it.

I had two partitions:
Vista System partition ~75GB
Files Partition ~75GB
And perhaps a small "unallocated space or two (couple MBs)

After Ubuntu install I have
Vista System Partition ~49GB
Files Partition ~ 51GB
Ubuntu Partition ~26GB (with ~1GB swap)
3 "Unallocated" spaces (same 2 small ones)....one of them is ~25GB

Somehow 25GB of space were severed from my "FILES" partition. I can't figure out how this happened, as I never invoked such an action. Also, my FILES partition has the "boot" flag on it, and not my "VISTA" partition...and I tihnk because of this I am unable to "Resize" it in Gnome Partition Editor.

...is it as easy as moving the boot Flag elsewhere? Or is that a really stupid thing to do?

Bottom line, I want my 25GB back on my "FILES" partition.

P.S. When in Vista, I can grow/shrink my "Vista" partition but not my "FILES" partition (same as in GParted when I'm booted in Ubuntu).

---

### Post by Ingenue on 2008-08-03
Are you booting your LiveCD then using GParted?

---

### Post by Meetloaf13 on 2008-08-03
That's a negative.  I'll try that and report back

---

### Post by mb_webguy on 2008-08-03
If it's a Dell laptop, it might have a MediaDirect(?) partition, which lets you do a fast boot into a stripped-down version of XP to quickly play music and movies without waiting for the main OS to boot.  This would explain the mystery boot partition.  Dell also creates a partition to restore your computer to the factory defaults.

But what does GRUB show when you boot your computer?

Anyway, you can use gparted to change around your partitions.  Vista's partition manager is crap.

---

### Post by cybrsaylr on 2008-08-03
Don't know why that happened. Whenever I dual booted Hardy with XP and Vista Ubuntu shared the C drive with windows and left the other partitons untouched. Since you installed it, it looks like you somehow lost that space on your drive.

---

### Post by Ingenue on 2008-08-03
> **mb_webguy said:**
> Anyway, you can use gparted to change around your partitions.  Vista's partition manager is crap.

I concur. Vista is out for Vista if you catch my drift. I have had really good experience with using GParted, I sucesfully  resized my Vista and Ubuntu partition with no data loss on either side.

---

### Post by Meetloaf13 on 2008-08-03
Thanks for helping out a n00b :D

That did the trick.

---

### Post by Ingenue on 2008-08-03
> **Meetloaf13 said:**
> Thanks for helping out a n00b :D

That did the trick.

Glad it helped!

---

