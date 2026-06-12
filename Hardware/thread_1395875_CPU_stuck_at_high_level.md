---
title: "CPU stuck at high level"
date: 2010-02-01
forum: Hardware
---

### Post by Pilch1989 on 2010-02-01
Hiya, I was wondering if anyone could help me. I am new to ubuntu, and I am running 9.10. Every so often my computer will become really unresponsive and when I look at the System Monitor one of the CPUs will be running at around 99%, and when I look it the processes section of the System Monitor there does not seem to be any reason why this should be happening. The computer always seems to go back to normal after I restart it though. Can anyone help identify why this is happening? Thanks very much.

---

### Post by pkm4o93 on 2010-02-03
> **Pilch1989 said:**
> Hiya, I was wondering if anyone could help me. I am new to ubuntu, and I am running 9.10. Every so often my computer will become really unresponsive and when I look at the System Monitor one of the CPUs will be running at around 99%, and when I look it the processes section of the System Monitor there does not seem to be any reason why this should be happening. The computer always seems to go back to normal after I restart it though. Can anyone help identify why this is happening? Thanks very much.
GNOME? 
Which processes are taking the cpu time?
I use Kubuntu 9.04 and notice that certain dolphin operations freeze my pc for ten seconds - so I use 'pcmanfm' for the moment.

It may be useful to redirect the output from TOP 

eg at commandline ```
top > log.txt
```
There is also a batch mode for logging top.

---

