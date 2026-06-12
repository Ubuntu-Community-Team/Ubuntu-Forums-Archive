---
title: "Kernel Editing to enable CPU Scaling?"
date: 2008-08-17
forum: General Help
---

### Post by davethewave83 on 2008-08-17
Can anyone tell me where to find the "kernel" and how to edit it to enable cpu frequency scaling?

I googled Ubuntu "how to edit the kernel"and there was no information on it

---

### Post by davethewave83 on 2008-08-18
bump

---

### Post by dexter on 2008-08-18
Try using the cpufreq utilities. They are installed by default.
cpufreq-info
cpufreq-selector
cpufreq-set

---

### Post by sdennie on 2008-08-18
Frequency scaling is enabled in the kernel for supported machines (which includes almost all newer machines).  As said above, try:

```

cpufreq-info

```

Also, make sure that you have the option enabled in your BIOS if it has an option to modify.

---

### Post by davethewave83 on 2008-08-19
Thanks! It wasn't installed by default though I had to apt-get install cpufrequtils.. also my bios has little features, it is a toshiba satellite 1415-s173, I would imagine it supports scaling as it is using a mobile cpu. I tried the commands, I just get errors: "analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU"
Thanks anyways for the reply :)

---

### Post by sdennie on 2008-08-19
Unfortunately, Toshiba has a very poor track record when it comes to linux.  Specifically, a number of their machines have BIOS problems where various features don't work correctly.  Yours is unfortunate but not fatal (like a non-working GPU fan has been to people in the past) but, I would see if you can find a BIOS update and see if that helps.

---

