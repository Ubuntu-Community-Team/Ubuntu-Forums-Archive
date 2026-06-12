---
title: "Boot from a hard drive which has 4 partitions (not immediately important)?"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by SBDxAric on 2009-02-17
This isnt immediately important, i know theres many more emergency situations...

But i have formatted my usb hard drive into 3 partitions:
J: FAT32 74.23 GB 60.80 GB PRIMARY
* UNALLOCATED 75.40 GB LOGICAL
K: UNFORMATTED 74.23 GB LOGICAL
L: UNFORMATTED 74.23 GB LOGICAL

J: Is my regualar backups and stuff

K: i plan to move wubi onto
L: I plan to install Leopard on it.

I just wanna know how i will choose what to boot from?
When i restart, will it go straight to K:, or will i have a choice K: or L:?

---

### Post by Mark Phelps on 2009-02-18
Basically, it will attempt to load the OS as directed from your MBR, so the last OS you install that updates the MBR will win -- because each one, unless you have options to choose otherwise, will overwrite the MBR when you install it.

---

### Post by SBDxAric on 2009-02-18
Is there any way to fix this? Or will it be randomized what will boot up?
Another question, will i have to make J: logical and not primary?

---

### Post by Mark Phelps on 2009-02-18
Fix what? I told you how the booted OS is decided -- by the last OS installed.  Can't answer a generic question about how to change that AFTER installation because it depends critically on what OS is last -- and you're talking about installing a Mac OS -- and this is the Ubuntu forum, not the Apple forum.

---

### Post by SBDxAric on 2009-02-19
I havent installed them yet... but ur right this isnt mac forums, sorry for troubling you. I will be off now :)

---

