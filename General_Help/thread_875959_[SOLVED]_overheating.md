---
title: "[SOLVED] overheating"
date: 2008-07-31
forum: General Help
---

### Post by vikasmk on 2008-07-31
My system sometimes shuts down automatically and on restart says that the processor got over heated. I checked my cooling fans , they're ok. could something else be the problem?????

---

### Post by Diabolis on 2008-07-31
1.- somethings is obstructing the fans. something like working over a soft surface, such as your bed, if we are talking about a laptop.

2.- high cpu usage.

type this in a terminal:
```
top
```

press **q** to exit.

This command show which processes are running and the percentage of cpu that each of them is using.

---

### Post by vikasmk on 2008-07-31
Mine's a desktop not a laptop..

```
Tasks: 104 total,   2 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.6%us,  1.3%sy,  0.0%ni, 92.7%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    513880k total,   505656k used,     8224k free,     9196k buffers
Swap:  1927760k total,    38180k used,  1889580k free,   191668k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 5203 root      20   0  222m  16m 8344 S  1.7  3.2   1:26.17 Xorg              
 6756 vikasmk   20   0  140m  55m  20m S  1.0 11.2   0:11.17 firefox           
 5592 vikasmk   20   0 25192  11m 8008 S  0.7  2.3   0:03.32 nm-applet         
 6892 vikasmk   20   0  2308 1100  852 R  0.7  0.2   0:00.16 top               
    1 root      20   0  2844 1692  544 S  0.0  0.3   0:01.28 init              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper           
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 kblockd/0         
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify      
  119 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod           
  156 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush           
  157 root      20   0     0    0    0 S  0.0  0.0   0:00.06 pdflush  
```
can someone see what the problem might be??:(

---

### Post by Diabolis on 2008-07-31
What you posted looks perfectly fine.

```

  PID USER      PR  NI  VIRT  RES  SHR S [COLOR="Red"]%CPU[/COLOR] %MEM    TIME+  COMMAND           
 5203 root      20   0  222m  16m 8344 S  [COLOR="Red"]1.7[/COLOR]  3.2   1:26.17 Xorg              
 6756 vikasmk   20   0  140m  55m  20m S  [COLOR="Red"]1.0[/COLOR] 11.2   0:11.17 firefox           
 5592 vikasmk   20   0 25192  11m 8008 S  [COLOR="Red"]0.7[/COLOR]  2.3   0:03.32 nm-applet         

```

Keep an eye on your computer and check the processes again once it gets really hot.

---

### Post by ingeva on 2008-07-31
> **vikasmk said:**
> My system sometimes shuts down automatically and on restart says that the processor got over heated. I checked my cooling fans , they're ok. could something else be the problem?????

The problem is that the processor doesn't get enough cooling. A modern processor can reduce the amount of energy used when it spends a lot of time in the idle loop, but I wouldn't focus too much on that.

My old computer was about 4 years old and started to get overheating problems. Even running the fans at full speed didn't help. there are three fans; one in the PSU, one on the processor and one in the cabinet. The last one started to make noise, and the processor fan turned out to have insufficient contact with the processor. Removing some of the cooling paste and making sure the connection was good, solved the problem.

Now I've delivered the computer for service so I can have the fans changed because they were really old and still noisy.

I wouldn't trust the fans too much if they are old (more than 3 years), or even if they are not noisy. Check the power they are consuming, and change them with fans that are not weaker, possibly a little stronger (The energy used is Voltage times Current).

---

