---
title: "Load_Cycle_Count hard drive health in Ubuntu 7.1 FAQ"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by goombamd on 2008-02-24
I'm wondering if anyone can help make an FAQ section for this issue that apparently drastically reduces your hard drive life.

1. Was this issue fixed in Ubuntu 7.1?

2. How do I install smartmontools? Click System --> Administration --> Synaptics Package manager. Search for smartmontools.

3. How do I check my hard drive's load_cycle_count?

Apparently you type the following in the terminal

sudo smartctl -a /dev/sda | grep Load_Cycle_Count

(This is my result.. apparently it's the last number. But, since this is a relatively new laptop, I doubt I've had 94489286958 cycles.  I'm wondering if the "-" means my load_cycle_count is unavailable.  But, i don't know what the long number on the next line means.. any help?)

225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       94489286958


4.  How do I fix the problem?


Thanks for your help all!

---

### Post by jespdj on 2008-02-25
The big thread about this problem is here:
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

Note that it is not a bug in Ubuntu, so it has not been fixed in Ubuntu 7.10.

---

