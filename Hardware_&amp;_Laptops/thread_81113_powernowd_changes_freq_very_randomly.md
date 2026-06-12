---
title: "powernowd changes freq very randomly"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by Asraniel on 2005-10-23
or can i say, not at all? well, SOMETIMES the freq changes. it can happen that i boot with 800 Mhz, one time i booted with 1500 mhz, and normaly with 1.86 ghz. and sometimes it can happen that the freq goes from 1.86ghz to 800 mhz. this happens once a day perhaps, and it wont jump back (well, at least i didnt observe it)

where are log messages and so about powernowd? any alternatives? if i uninstall powernowd he also wants to remove kubuntu-desktop, and i dont want that of course

---

### Post by mjwood0 on 2005-10-24
Sounds to me like you have the wrong speedstep module loaded.

More info is needed to really understand the problem though.

What type of processor? (more /proc/cpuinfo)

And what module is currently loaded? (more /proc/ioports)

---

### Post by Asraniel on 2005-10-24
its a centrino, my laptop is a acer travelmate 8103.

more /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.86GHz
stepping        : 8
cpu MHz         : 797.924
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 1576.09

and here the other one:

more /proc/ioports
0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : libata
01f0-01f7 : libata
02f8-02ff : serial
0378-037a : parport0
037b-037f : parport0
03c0-03df : vga+
03f8-03ff : serial
0778-077a : parport0
1000-107f : motherboard
  1000-1003 : PM1a_EVT_BLK
  1004-1005 : PM1a_CNT_BLK
  1008-100b : PM_TMR
  1010-1015 : ACPI CPU throttle
  1020-1020 : PM2_CNT_BLK
  1028-102f : GPE0_BLK
1180-11bf : motherboard
1600-167f : motherboard
1800-181f : 0000:00:1d.0
  1800-181f : uhci_hcd
1820-183f : 0000:00:1d.1
  1820-183f : uhci_hcd
1840-185f : 0000:00:1d.2
  1840-185f : uhci_hcd
1860-187f : 0000:00:1d.3
  1860-187f : uhci_hcd
18a0-18af : 0000:00:1f.2
  18a0-18af : libata
18e0-18ff : 0000:00:1f.3
2000-2fff : PCI Bus #01
  2000-20ff : 0000:01:00.0
4000-40ff : PCI CardBus #07
4400-44ff : PCI CardBus #07
4800-48ff : PCI CardBus #0b
4c00-4cff : PCI CardBus #0b
5000-50ff : PCI CardBus #0f
5400-54ff : PCI CardBus #0f


I have no idea wich speedstep module is loaded, but your help would be great!!!!!

---

### Post by mjwood0 on 2005-10-24
To find out what module you have loaded, you would type lsmod. It shoudl show something like speedstep_xxx

I'm not sure which one you need for your processor, but powernowd incorrectly identified mine which caused weird behavior.

---

### Post by Asraniel on 2005-10-24
this is what it gives me:

lsmod | grep speedstep
speedstep_centrino      7636  1
freq_table              4388  2 speedstep_centrino,cpufreq_stats
processor              22812  2 speedstep_centrino,thermal


seems right? i think

---

### Post by mjwood0 on 2005-10-24
Hmm..

That does appear correct.  There's another thread about the Centrino somewhere but I'm at work and don't have the info.  You can also go to the bugzilla.ubuntu.com and search for powernowd.  Perhaps someone else is experiencing the same problem.

---

