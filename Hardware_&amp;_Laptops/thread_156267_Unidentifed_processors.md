---
title: "Unidentifed processors???"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by LostinTime on 2006-04-06
While I am a relative noob to linux.  I had no problems with 5.04.(the following did show up correctly under 5.04)

**Under 5.10, my processors show up as unknown in device manager.  They are standard PIV Xeons with HT (533 Mhz 2.4 Ghz Prestonia M0 Cores  (They are NOT mobile or low voltage xeons).  5.10 was completely clean install.**

I am running 2.6.12-10-686-smp (2.6.12-10.30).  All four proessors do show up.  But why are they now UNKNOWN. 

Please be specific on any instructions on how to correct this problem.

Thanks in advance. Anyone?

---

### Post by LostinTime on 2006-04-07
bump

---

### Post by hajk on 2006-04-08
Doesn't look like a Ubuntu problem, it's the kernel that does not recognize the Xeons, at least not with the stock kernel that you're running.

You might consider compiling a new kernel with processor configuration that more closely matches your hardware. Use the Search function to get some idea on how to do this. And then you could also ignore the "problem" if the kernel functions OK otherwise.

<smug>My two Opteron cores are correctly identified by stock Ubuntu amd-k7 kernel...</smug>

---

### Post by ghakko on 2006-04-08
The "Device Manager" is actually a front-end to HAL, which isn't too smart about enumerating processors.

Use "cat /proc/cpuinfo" or "lshw" instead.

---

