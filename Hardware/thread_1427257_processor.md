---
title: "processor"
date: 2010-03-11
forum: Hardware
---

### Post by msidhard on 2010-03-11
friends i am using p4 2.8GHz processor. but my windows and ubuntu both says it is celeron 1.8GHz processor. i opened my cpu and removed the processor fan and confirmed that it is p4 processor. during booting in cmos screen i see pentium processor 2.8GHz . what is the problem how could i recover from it. thankz in advance>

---

### Post by MonsterTrimble on 2010-03-11
Did you just notice this? Or did something change recently on your system?

---

### Post by akand074 on 2010-03-11
hmm... could be that your idle frequency is 1.8Ghz, my processor is at 2.8ghz but it reads it as 1.2ghz in some applications because thats the idle frequency. Just a guess.

---

### Post by era86 on 2010-03-11
> **msidhard said:**
> friends i am using p4 2.8GHz processor. but my windows and ubuntu both says it is celeron 1.8GHz processor. i opened my cpu and removed the processor fan and confirmed that it is p4 processor. during booting in cmos screen i see pentium processor 2.8GHz . what is the problem how could i recover from it. thankz in advance>

What software are you using to detect the CPU?  cpu-z?  What is the model of the CPU?

---

### Post by cascade9 on 2010-03-11
With both linux and windows agreeing, then I think you do have a celeron 1.8Ghz. There is a chance that you've got a hardware problem. But....I'm sorry to say...I think you've been sold a 'fake' (remarked) CPU- 

> **We have recently discovered that a chinese manufacturer is selling large quantities of fake Intel Pentium 4 CPUs. The manufacturer re-labels Intel Celeron CPUs and sells them, in a motherboard+CPU combo, as Pentium 4 2.8/3.6GHz original CPUs.** [http://www.cdrinfo.com/forum/tm.asp?m=121030&mpage=1&key=&#121030](http://www.cdrinfo.com/forum/tm.asp?m=121030&mpage=1&key=&#121030)

Yep, a 2005 post- but teh people behind them were still around in 2008, and they actually have the....er....honesty? (I spose 'cojones' is a bit too rude if  said in english)  to list them as 'remarked'. Avaible in both SIS and Intel chipset motherboards. 

> P4/2.8G CPU:
Brand new.remarked from Celeron/1.7G.&#8221;P4/2.8G&#8221; printed on cpu top[http://www.ecplaza.net/product/73975_149208/motherboard_cpu_combo.html](http://www.ecplaza.net/product/73975_149208/motherboard_cpu_combo.html)

> Intel 845GL MB + P4/3.6G combo - Hot Sales! (P4/2.6/3.2G is optional). Intel 845GL motherboard: 1) Micro-ATX. PGA478 400/533MHz ; 2) Integrated Intel extreme graphics and AC'97 audio ; 3) Supports DDR333/266/200 ; 4) Supports UltraDMA 100/66 ; 5) Retail box, brand new with CD / manual / cable. P4/3.6G CPU: Brand new, remarked from Celeron, "P4/3.6G" printed on CPU top.exactly same as original P4 cpu. CPU show P4/3.6G for boot screen and Wdows/XP both(with software CD)[http://www.trader-china.com/Computer-Software/Hardware-Components/P4-MB-CPU-combo-l18371.html](http://www.trader-china.com/Computer-Software/Hardware-Components/P4-MB-CPU-combo-l18371.html)

Edit for mods- yeah, I'm half expecting the spanish to be edited, but as far as I know its not considered as rude in spanish speaking countries as the english for the same term is in english speaking countries. If its deemed offensive, go ahead, edit it. If any users find it offensive, you need only PM me and I will remove it ;)

---

### Post by era86 on 2010-03-11
ouch...

---

### Post by Phrea on 2010-03-11
The BIOS however does seem to recognize it as a 2.8GHz cpu [be it a Celeron or a P4].
It might be that you've got a 2.8GHz Celeron.

Post what CPUZ says about it.

---

### Post by akand074 on 2010-03-11
see what this says:

```
sudo apt-get install hardinfo
```

There it shows my CPU name where it shows 2.8GHz but the actual frequency it records shows 1197.00MHz, because that's the idle core speed.

---

### Post by msidhard on 2010-03-12
Actually friends i assembled the system a week back. I confirmed that the processor is p4 2.8 ghz. The bios also recognises that it is p4 processor. I could.nt identify the make of mother board.

---

### Post by cascade9 on 2010-03-12
> **msidhard said:**
> Actually friends i assembled the system a week back. I confirmed that the processor is p4 2.8 ghz. The bios also recognises that it is p4 processor. I could.nt identify the make of mother board.

Writing on the top, and the BIOS saying its a 2.8Ghz P4 doesnt mean its a P4. When windows and Linux agree on something, I'd go with what they say. 

Try both of these commands and post the output- 

grep "model name" /proc/cpuinfo
[FONT=monospace]lscpu[/FONT]

Eg- if its socket 478, there is only 2 celeron 1.8Ghz chips. Both 400Mhz FSB/128K cache chips. P4 2.8 had various models, in 400, 533 and 800Mhz FSB, but they all had 512K cache or more. 

So if lscpu outputs "L2 cache: 128K" then its a celeron, 100% for sure.

---

### Post by msidhard on 2010-03-13
result for grep "model name" /proc/cpuinfo:
model name	: Intel(R) Celeron(R) CPU 1.80GHz
result for lscpu:
Architecture:          i686
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            15
Model:                 2
Stepping:              9
CPU MHz:               1804.196

---

### Post by cascade9 on 2010-03-13
Sure looks like a celeron to me. 

The 'lscpu' output looks shortened though, I get this-

```
Architecture:          x86_64
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            15
Model:                 107
Stepping:              2
CPU MHz:               2499.854
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
```

The L2 cache is what will tell me for sure if its a celeron, or if its some other problem.

---

