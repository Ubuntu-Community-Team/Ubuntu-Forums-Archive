---
title: "AMD Overclocking CPUINFO Incorrect"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by FLeiXiuS on 2005-07-11
Well yes I do have to say I've gone through the almight and overclocked my system last night.

Specs:
Asus A8N-SLI Deluxe
AMD 64 3200+ 2.0Ghz Winchester 90nm DIE
1GB Corsair XMS Pro DDR400 2-2-2-5
BFG Geforce 6600GT OC PCI-E
36.6GB Western Digital 10,000RPM
400GB Maxtor 7200RPM

Well so let me explain what I did...

Hyper Transport Multiplier: 3x
CPU Frequency: 355Mhz
CPU Multiplier: 9x
Chipset Voltage: 1.63v

Totalling: 3195Mhz
An overclock of 1195Mhz, woah I'm good :-P

Well the cmos said so and so did the bios.  So I figured, woot, yah know?  Well turns out when I `cat /proc/cpuinfo` to check my lovely perfomance, I'm getting 1.8Ghz with 3600 bogomips.

Anyone have any idea's on what would've caused this issue to be incorrect?

---

### Post by ene_dene on 2008-06-22
I have the same problem 3 years later.:) But on my Intel CPU it shows the right frequency.

---

### Post by robert shearer on 2008-06-22
I have just installed Hardy on an AMD 64 3000+ and find that the cpu is reported at half speed.

~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 12
model name	: AMD Athlon(tm) 64 Processor 3000+
stepping	: 0
cpu MHz		: 1000.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up ts fid vid ttp
bogomips	: 2011.08
clflush size	: 64

what is going on??? no overclocking just a normal install.Do I need a 64 bit o/s to get the full 2Ghz??

---

### Post by bikeboy on 2008-06-22
CPU scaling due to low load most likely. Right-click a panel and select 'Add to panel'. In there you will find the 'CPU Frequency Scaling Monitor' which should help you find what pecentage your CPU is running at. If it does turn out to be scaling down there are ways you can more finely control how it performs.

---

### Post by ene_dene on 2008-06-22
Robert, try writing in console:
```
sudo cpufreq-selector -g performance
```
And then try and see the cpuinfo.

---

### Post by robert shearer on 2008-06-22
Yes that now shows 2Ghz and yes the freq scaling applet does report this, now how do I reset it back to automatic scaling ?

---

### Post by robert shearer on 2008-06-22
Well, a reboot seems to have done the trick, or at least the freq scaling applet now shows variation from 1 to 2 Ghz. Thanks all.

---

### Post by ene_dene on 2008-06-22
> **robert shearer said:**
> Well, a reboot seems to have done the trick, or at least the freq scaling applet now shows variation from 1 to 2 Ghz. Thanks all.
I think that default option is "ondemand" which means that frequency will be available as you use processor, low freq on idle, and high on intensive tasks. There are few other governors (performance, powersave, ondemand...) which you can use if they suite you more.

---

