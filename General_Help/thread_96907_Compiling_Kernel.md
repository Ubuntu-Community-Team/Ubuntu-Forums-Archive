---
title: "Compiling Kernel"
date: 2005-11-29
forum: General Help
---

### Post by Anguis on 2005-11-29
Hi everyone

It seems that whenever I try to compile a kernel, my laptop (Toshiba Satellite A70) shuts itself off.

I've tried making the compilation nicer (nice -n19 make bzImage install modules modules_install), didn't help at all.  Tried booting with acpi off, that didn't help either.  I don't know what else to try.  Anyone have any ideas?

---

### Post by Rob2687 on 2005-11-29
Do you mean it shuts off during the compile process?

---

### Post by Anguis on 2005-11-29
[QUOTE=Rob2687]Do you mean it shuts off during the compile process?[/QUOTE]

Exactly, the computer shuts off completely without warning.

---

### Post by RAOF on 2005-11-29
Does the same thing happen with other computationally intensive & protracted tasks (like video transcoding)?  Re-nicing the kernel compile process won't actually change how much processor time it uses, just how easy it is for other processes to grab the cpu from it.  (Actually, that's not quite true - your power-management should throttle the CPU if no normal priority (nice 0 or lower) tasks want the CPU).

Compiling the kernel is actually a great stability-check benchmark... lots of disc access, CPU time, iterating over a **lot** of in-memory structures.  However, I don't think there's anything special in there which would cause your computer to shut down - crash with a segfault, yes.  Just shut down?  No.

---

### Post by Anguis on 2005-11-29
[QUOTE=RAOF]Does the same thing happen with other computationally intensive & protracted tasks (like video transcoding)? [/QUOTE]

Now that you mention it, this does happen sometimes on other things that are computationally intensive, but not with any amount of consistency.  So far, compiling the kernel is the only task that was able to reproduce this.

---

### Post by RAOF on 2005-11-29
In that case, I'd suggest looking for a heat-related cause.  Your laptop almost certainly has a temperature-based automatic shutdown, to stop your processor frying like an egg should something go wrong with the cooling.  Maybe your fans aren't working, or something?

---

### Post by az on 2005-11-29
Whenever I customise an old peice of hardware with some new heatsink or fan, I run it trough a kernel compilation to see if it holds up.  It is a great benchmark of cpu work.

---

### Post by akiro.yamamoto on 2005-11-29
What a stress test :smile:

---

