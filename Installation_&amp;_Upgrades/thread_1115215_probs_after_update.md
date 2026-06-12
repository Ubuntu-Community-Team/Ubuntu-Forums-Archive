---
title: "probs after update"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by vblanche on 2009-04-03
Hello,

I have XP pro 32-bit and Kubuntu 32-bit i dual boot. I recently booted in kubuntu, Adept installer did an update but then got error messages (can't remember exactly what they were), I restarted pc, got a message of serious crash error message of KDE4, when I try to open disk management, I'm getting this message: " There are no filesystems which you are allowed to mount or unmount.
Contact your administrator" .

Should I do a clean re-installation? if yes, how?

thanks
vini

---

### Post by Pumalite on 2009-04-03
If you want to do a clean install; use the old partitions. Install, go 'Manual' and pick the partitions. You can ignore /swap. If you have a separate /home; give it a mount point, but DON'T FORMAT IT

---

### Post by vblanche on 2009-04-04
thanks for reply. but i'm not sure I understood you.

I put the install cd, restart pc, and use same partitions and re-install over them?

sorry for my newbie questions.

thanks

---

### Post by cariboo on 2009-04-04
I would suggest you boot in recovery mode and once at the menu select drop to root prompt. At the prompt type:

```
apt-get install -f
```

then

```
apt-get update && apt-get dist-upgrade
```

Jim

---

