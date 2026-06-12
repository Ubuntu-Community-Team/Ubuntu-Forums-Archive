---
title: "Add a Floppy Drive in Hardy Heron"
date: 2008-10-22
forum: General Help
---

### Post by rheide on 2008-10-22
This should be an easy task but so far I haven't found a solution.

I have Hardy Heron installed via an ISO for EMC2 (a CNC tool). My guess is that the ISO needed room and removed packages necessary for floppy drive support.

So, the question is, how do I install the packages necessary to make the floppy work?

---

### Post by dcstar on 2008-10-23
> **rheide said:**
> This should be an easy task but so far I haven't found a solution.

I have Hardy Heron installed via an ISO for EMC2 (a CNC tool). My guess is that the ISO needed room and removed packages necessary for floppy drive support.

So, the question is, how do I install the packages necessary to make the floppy work?

I doubt that it is packages, it is more likely a hardware module (not) complied into the kernel.

AFAIK floppy support is still native and should be automatically detected by any standard Ubuntu kernel.

---

### Post by cariboo on 2008-10-23
Make sure the floppy module is inserted, to check, in a terminal type:

```
lsmod | grep floppy
```

I know at one time the floppy module was inserted by default, I used to blacklist it as I haven't used a floppy drive for years.

Jim

---

