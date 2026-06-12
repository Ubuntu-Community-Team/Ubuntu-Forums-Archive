---
title: "[SOLVED] CPU speed?"
date: 2008-06-30
forum: Hardware
---

### Post by Kinetic777 on 2008-06-30
My Processor doesn't seem to be working as fast as it should. As it is at 2.79Ghz (P4), it should be fast, and I have enough RAM. What I think is wrong is that my motherboard may not support such a high speed. The motherboard is in a Dell Dimension 2400 desktop. S/N is 411726100004. If anyone knows what the max CPU speed for that motherboard is, or can direct me to anything useful, I would be very happy  :grin:


-Solved it, Ubuntu was only permitting 75% of the CPU to be used. So I just switched it to use 100%. Works fine now.

---

### Post by sdennie on 2008-07-01
Try the following to get good information about your CPU:

```

sudo apt-get install cpufrequtils
cpufreq-info

```

If that doesn't work, try:

```

cat /proc/cpuinfo

```

And look for the CPU speed.

---

