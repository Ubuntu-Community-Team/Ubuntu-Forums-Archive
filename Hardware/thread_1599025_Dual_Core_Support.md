---
title: "Dual Core Support"
date: 2010-10-17
forum: Hardware
---

### Post by monkeypigs on 2010-10-17
Hi, 

I have just installed Ubuntu 10.10 on an intel dual core processor and it only seems to recognise one. System monitor only shows one processor. Now when I had Windows (and more recently FreeNAS) on this box, it showed as dual core so can anyone tell me where I'm going wrong? 

Here are a couple of results from other posts I've found
```
cat /proc/cpuinfo | grep name

model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
```

```
uname -a

Linux Ubuntu 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux
```

I've seen old posts about modifying /etc/init.d/rc to set CONCURRENCY=shell but as far as I can see these are outdated now. 

Many thanks!
Iain

---

