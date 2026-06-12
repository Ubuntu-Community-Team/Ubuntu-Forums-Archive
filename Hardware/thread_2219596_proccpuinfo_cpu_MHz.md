---
title: "/proc/cpuinfo cpu MHz"
date: 2014-04-24
forum: Hardware
---

### Post by rustybutt on 2014-04-24
I've got a machine with an AMD FX(tm)-6100 Six-Core Processor.  Why is it that /proc/cpuinfo reports that 5 of my 6 cores runs only at 1400 MHz and one core runs at 3300 MHz?


$ cat /proc/cpuinfo | grep MHz
cpu MHz         : 1400.000
cpu MHz         : 1400.000
cpu MHz         : 1400.000
cpu MHz         : 3300.000
cpu MHz         : 1400.000
cpu MHz         : 1400.000

---

