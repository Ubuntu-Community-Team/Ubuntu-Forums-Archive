---
title: "Stated kernel speed not up to expectations"
date: 2014-11-23
forum: Hardware
---

### Post by Paul King on 2014-11-23
First, here is a short summary of my Haskell Intel Core i7, as parsed from /proc/cpuinfo:

CPU Maker:  GenuineIntel
CPU Model:  Intel(R) Core(TM) i7-4770K CPU @ 3.50GHz
Proc Speed (MHz):  800.000
bogomips:  6999.92
Number of Processors: 8
Number of Cores: 4

Note the radical discrepancy between the advertised CPU speed (3500 MHz) and the reported processor speed by the kernel: (800 MHz). There is obviously a problem here. I am getting one-fourth of the speed I should be getting. On most websites I have seen, they should be at least close, but not orders of magnitude apart.

Is there any way I can coax the correct speed in my copy of Ubuntu Studio (version 14.04)? It would seem that the default kernel that came with Ubuntu Studio may not even be the correct kernel. My CPU has 4 cores and full hyperthreading. Do I need to compile my own from scratch?

PJK

---

### Post by Doug S on 2014-11-23
The cpu clock frequency reported is just its frequency at the time you looked at /proc/cpuinfo. There is little load, so the frequency has been throttled back to minimum to save power. Load up your system and try again and you will observe a higher clock frequency.

Edit: Example (my processor minimum is 1600 MHz, max 3.4 GHz and turbot 3.8 GHz):```
doug@s15:~/temp$ cat /proc/cpuinfo | grep MHz
cpu MHz         : 1627.750
cpu MHz         : 1627.750
cpu MHz         : 1627.750
cpu MHz         : 1627.750
cpu MHz         : 1627.750
cpu MHz         : 1627.750
cpu MHz         : 1627.750
cpu MHz         : 1627.750
```Now load up CPU 7```
doug@s15:~/temp$ cat /proc/cpuinfo | grep MHz
cpu MHz         : 3699.625
cpu MHz         : 3699.625
cpu MHz         : 3699.625
cpu MHz         : 3805.875
cpu MHz         : 3699.625
cpu MHz         : 3699.625
cpu MHz         : 3699.625
cpu MHz         : [COLOR=#ff0000]3805.875[/COLOR]
```Note: Depending on which cpu frequency governor you are using your results may look different (I am using the intel_pstate driver).

---

### Post by Paul King on 2014-11-23
Ah, I see. The processor speed now reads 2000. Thanks, Doug S.!

PJK

---

