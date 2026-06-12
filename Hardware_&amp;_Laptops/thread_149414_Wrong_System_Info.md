---
title: "Wrong System Info"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by hossmar on 2006-03-23
Hi! I recently installed Ubuntu on a Compaq Presario 2701T but the System Info regarding the Cpu Freq and the Memory Size is wrong. 

When I execute  "sudo head /proc/cpuinfo" I get:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 11
model name      : Intel(R) Pentium(R) III Mobile CPU       933MHz
stepping        : 1
cpu MHz         : 930.339
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no

But the processor speed is 1.3Ghz

Also when I execute "top" I get:

Tasks:  77 total,   2 running,  75 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.7% us,  1.7% sy,  0.0% ni, 86.3% id,  1.0% wa,  0.3% hi,  0.0% si
Mem:    126200k total,   123656k used,     2544k free,     1364k buffers
Swap:   498004k total,   126440k used,   371564k free,    31632k cached

But the real memory size is 512Mb. The operating system is running really slow ](*,) , I need some help please! :confused:

---

### Post by taurus on 2006-03-23
What kernel did you use?  Run these two commands from a terminal and paste the outputs here then...
```

uname -a
free

```

---

