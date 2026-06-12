---
title: "Finding processor"
date: 2009-06-22
forum: Hardware
---

### Post by Jestersage on 2009-06-22
Recently, I purchase a second hand board from FreeGeek, and the volunteer say it is a sempron. However, when i booted it up, all it say is "AMD Hammer - model unknown" in both BIOS boot and Ubuntu 9.04.

All I can confirm is that it is a Socket 754 board ([COLOR=#fd6724]GA-K8NS Pro to be precise)[/COLOR].

So is it a Sempron 3100+, or could it be a full fledge A64? If so, how should I check?

P.S. As for the cost in total: $40 for that MB + CPU + 512mb + 32mb TNT2 + 8 bay server case. Not a bad deal, no?

---

### Post by robert shearer on 2009-06-22
What does 

```
cat /proc/cpuinfo
```

output?

---

### Post by Jestersage on 2009-06-22
> **robert shearer said:**
> What does ```
cat /proc/cpuinfo
```output?

CPU family: 15
model: 44
model name: AMD Hammer Family processor - model unknown
stepping: 2
cpu Mhz: 1872.138
cache 256kb

Base on this, it seems likely to be a Sempron 3100+.

**Also**, I know some model of sempron 3100+ Socket 754 is 64 bits. How do i check for it?

---

### Post by robert shearer on 2009-06-22
> **Jestersage said:**
> 
stepping: 2
cpu Mhz: 1872.138
cache 256kb
Socket 754 


This page may be of help..
[http://www.cpu-world.com/info/AMD/Athlon-model-number.html](http://www.cpu-world.com/info/AMD/Athlon-model-number.html)

I don't think that any of the 64bit have less than 512kb L2 cache ?.

---

### Post by robert shearer on 2009-06-22
After a little hunting this page may be what you need to check the cpu 32 vs 64 bit.

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

and the second method on this page works for me..
[http://blogs.koolwal.net/2009/03/17/tip-how-to-tell-whether-your-system-is-32-bit-or-64-bit-in-linux/](http://blogs.koolwal.net/2009/03/17/tip-how-to-tell-whether-your-system-is-32-bit-or-64-bit-in-linux/)

---

### Post by Jestersage on 2009-06-22
Thanks everyone. It seems like it's 64 bit capable.

So how do I edit the title so that it is "[SOLVED]"?

---

### Post by robert shearer on 2009-06-22
> So how do I edit the title so that it is "[SOLVED]"?

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

