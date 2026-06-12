---
title: "Benchmark APP??"
date: 2010-01-23
forum: Hardware
---

### Post by NiGhtMarEs0nWax on 2010-01-23
Hi, is there a package in the repos to benchmark my hardware **_and_** compare it to an online database of other hardware profiles?

id prefer an app that doesn't give some abstract result in the form of a single number, but something that gives MIPS, FLOPS. bandwidth, read/write speeds etc.  Preferably for all the devices in my system.

Thanks!

---

### Post by warfacegod on 2010-01-23
Try:

```
sudo apt-get install hardinfo
```

I don't know if it will connect to the net but it looks like it will show you the information you want.

---

### Post by warfacegod on 2010-01-23
Here's a copy of my benchmark results.

Benchmarks
CPU Blowfish
CPU Blowfish
This Machine	2793 MHz	10.996
Intel(R) Celeron(R) M processor 1.50GHz	(null)	26.1876862
PowerPC 740/750 (280.00MHz)	(null)	172.816713
CPU CryptoHash
CPU Cryptohash
This Machine	2793 MHz	79.016
CPU Fibonacci
CPU Fibonacci
This Machine	2793 MHz	4.657
Intel(R) Celeron(R) M processor 1.50GHz	(null)	8.1375674
PowerPC 740/750 (280.00MHz)	(null)	58.07682
CPU N-Queens
CPU N-Queens
This Machine	2793 MHz	14.719
FPU FFT
FPU FFT
This Machine	2793 MHz	5.893
FPU Raytracing
FPU Raytracing
This Machine	2793 MHz	63.260
Intel(R) Celeron(R) M processor 1.50GHz	(null)	40.8816714
PowerPC 740/750 (280.00MHz)	(null)	161.312647

---

### Post by NiGhtMarEs0nWax on 2010-01-23
Thanks for the reply but i find that app rather unhelpful, all it does is give me either a clock rate or an abstract score. i was looking for something that can give clear benchmark results, with respect to instructions per second, cycles, bandwidth, read/write times etc. something useful to benchmark overclocks, and can be compared with otehr system profiles.

---

### Post by warfacegod on 2010-01-23
[http://lbs.sourceforge.net/]("http://lbs.sourceforge.net/")

---

### Post by NiGhtMarEs0nWax on 2010-01-23
Thanks man! I'll give them a  try tomorrow.


Thanks.

---

