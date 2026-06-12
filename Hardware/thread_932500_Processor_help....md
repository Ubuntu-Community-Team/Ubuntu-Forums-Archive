---
title: "Processor help..."
date: 2008-09-28
forum: Hardware
---

### Post by zeryth on 2008-09-28
HelloHello!

I have recently installed ubuntu i386 on my msi k8n neo2 platinum motherboard, but i should have chosen the AMD version, but i am not so sure about that because of this:
> What type of computer do you have?
Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
 64bit AMD and Intel computers 

oh, btw, i have the default processor...

Bye!

---

### Post by cariboo on 2008-09-28
You really did not give us enough info to diagnose your problem. In a Applications-->Accessories-->Terminal type:

```
cat /proc/cpuinfo
```

The output should look something like this:

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 2009.123
cache size	: 512 KB
```

The above is only a short snippet of the complete output. If you could post the output of the above command. We can tell you what versions you can install.

Jim

---

### Post by zeryth on 2008-09-28
>  cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 39
model name	: AMD Athlon(tm) 64 Processor 3700+
stepping	: 1
cpu MHz		: 2211.377
cache size	: 1024 KB

here's the info, sorry for not giving you more info ^^

---

