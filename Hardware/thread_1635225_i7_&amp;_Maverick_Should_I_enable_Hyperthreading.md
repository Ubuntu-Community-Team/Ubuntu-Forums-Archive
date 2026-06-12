---
title: "i7 &amp; Maverick: Should I enable Hyperthreading?"
date: 2010-12-01
forum: Hardware
---

### Post by phlibi on 2010-12-01
Hi folks,

I've recently seen the Hyperthreading-Option in my BIOS (Thinkpad W510 with Intel i7, 4x1.73GHz). I wonder now if it makes sense to have HTT enabled if the CPU itself consists of four cores already. I've ran a few benchmarks with different thread counts to see how the Processor does with HTT enabled and disabled:
```

HT On:

sysbench --num-threads=1 --test=cpu --cpu-max-prime=10000 run
9.3111s
sysbench --num-threads=2 --test=cpu --cpu-max-prime=10000 run
5.7431s
sysbench --num-threads=4 --test=cpu --cpu-max-prime=10000 run
3.2829s
sysbench --num-threads=8 --test=cpu --cpu-max-prime=10000 run
2.7434s

HT Off:

sysbench --num-threads=1 --test=cpu --cpu-max-prime=10000 run
8.6214s
sysbench --num-threads=2 --test=cpu --cpu-max-prime=10000 run
4.8815s
sysbench --num-threads=4 --test=cpu --cpu-max-prime=10000 run
3.3669s
sysbench --num-threads=8 --test=cpu --cpu-max-prime=10000 run
3.4006s

Threads     HT On   HT Off
1           100%     92.6%
2           100%     85.0%
4           100%    102.7%
8           100%    124.1%

```

As can be seen, HTT is useful if there are several threads involved (surprise, surprise...), but it can decrease performance of single threads.
My question is, if it is good to have HTT enabled when running Ubuntu. According to
[http://www.intel.com/support/processors/sb/CS-017343.htm](http://www.intel.com/support/processors/sb/CS-017343.htm)
it is not certified as a Hyperthreading-OS. But I can't really believe that it has less built-in support for this technology than, for example, Red Hat.

So does anyone know if HTT should be enabled? Or do you have any experiences regarding this option?

Thanks and best regards,
Philipp

---

