---
title: "identifying my processor?"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by Big_Croc7 on 2007-06-05
Hi, I've a slightly odd question - I've got a pc and I don't know what processor it's using.  How can I identify it?  It seems to be a non-standard one, or not recognised properly, or something - I've tried device manager, but no information is given.

Here's the ouput from cat /proc/acpi/processor/CPU1 (the only directory under processor):

processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no

Any suggestions?

---

### Post by IntuitiveNipple on 2007-06-05
In  /proc/acpi/processor/ the CPU numbering usually starts at 0, so unless you have a multi-core or dual-CPU system CPU1 might not show much. On a dual-CPU PC you might see:
```
$ ls /proc/acpi/processor/
CPU0  CPU1
$ ls /proc/acpi/processor/CPU0
info  limit  power  throttling
```
Do you get anything better using:
```
$ cat /proc/cpuinfo
```

---

### Post by Big_Croc7 on 2007-06-05
Oh yes - the second one (/proc/cpuinfo) works fine.  Brilliant, thanks!

I'm puzzled now though - why don't I have a CPU0 directory?

---

