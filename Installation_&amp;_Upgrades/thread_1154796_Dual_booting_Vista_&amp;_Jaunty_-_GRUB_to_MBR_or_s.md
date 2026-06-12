---
title: "Dual booting Vista &amp; Jaunty - GRUB to MBR or sda2?"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by pedrogent on 2009-05-10
Here's a really simple question. I hope someone has a simple answer.

I've set up dual boot systems with the above combination many times. Vista is already installed. I use the 'alternate' Ubuntu install disc.

I can never remember where I should be placing GRUB (and as a consequence I usually need to bust out the ol' Super Grub Disk and then use EasyBCD).

In the end, my primary HDD will be partitioned as follows:

sda1 = Vista
sda2 = /
sda3 = swap

So: Should I write GRUB to the MBR (as the install disc recommends) or should I write it to sda2 (where Ubuntu will be installed)?

If I write it to sda2, will GRUB somehow still take first place in the scheme of things?

I hope this is clear. Thanks in advance.

---

### Post by pedrogent on 2009-05-10
Sorry to bump this... but someone must know the answer... and I'm just about to pull the trigger.

When I install Ubuntu do I install GRUB into the MBR or onto /dev/sda2 (where Ubuntu will be installed)?

:confused:

---

### Post by louieb on 2009-05-10
Depends on which boot loader you want to come up when the computer boots.

GRUB - install to MBR (default)

Vista's boot loader - install to sda2. Then use EasyBCD to get a Ubuntu option in Vista's boot loader.

---

### Post by pedrogent on 2009-05-10
Thanks very much my friend.

---

