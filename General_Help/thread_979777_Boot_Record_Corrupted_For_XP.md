---
title: "Boot Record Corrupted For XP"
date: 2008-11-12
forum: General Help
---

### Post by Peter6218 on 2008-11-12
I have a system with two hard drives. One HD has Win XP-SP3, the other HD has Ibex.

Every time I go to Ibex via grub the boot record on the other HD is being corrupted.

This has happened time and again.

If you want to think of the drives as letter:

C: Ibex 8.10
D: Win XP-SP3

On another system using the same setup arrangement the Win boot has been corrupted once but that's all. Fixed that problem and it seems fine since then.

Ideas??

---

### Post by Peter6218 on 2008-11-17
Well that's fixed. Totally my own fault.

Both HD's had been slaves in other machines and I forgot to move the jumper to Master on the first in the chain.

Interesting effect though as I ended up having to format D: and then reload XP. All is well now.

---

