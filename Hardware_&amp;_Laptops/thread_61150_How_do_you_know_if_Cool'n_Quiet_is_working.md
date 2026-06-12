---
title: "How do you know if Cool'n Quiet is working?"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by Adam Lee on 2005-08-30
Hi there : ) 
I use an AMD64 and Cool'n Quiet works great on Windows.
However since I'm a Linuxer now and was wondering if it's working.

adam@ubuntu:~$ sudo cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 31
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 0
cpu MHz         : 1803.700
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 3563.52

This is output of 
cat /proc/cpuinfo 
and it says cpu MHz is 1803.700...and I only have a terminal and Firefox opened. 

Does anyone willing to give out some help?

Thank you

---

### Post by ubuntme on 2005-08-30
Is there any noise difference from windows to linux?

The cpu fan should be quiet when idling, and louder under load, if the fan is spinning about the same between windows and lnux I would assume its working.  Actually, It should be cooler and quieter under linux than windows when idling.

---

### Post by Adam Lee on 2005-08-31
[QUOTE=ubuntme]Is there any noise difference from windows to linux?

The cpu fan should be quiet when idling, and louder under load, if the fan is spinning about the same between windows and lnux I would assume its working.  Actually, It should be cooler and quieter under linux than windows when idling.[/QUOTE]

hm I don't think there is any difference at all. And I know this because I really do pay attention to the noise my system makes. 

Well, anyways, I found by running "cat /proc/cpuinfo", the frequency was about 1000Mhz this afternoon(about 5 hours ago). But now my CPU in running at its full speed, and I'm not even doing anything. I checked the process monitor, and CPU usage is mostly 1~2%. 

However, the funny thing is that while "cat /proc/cpuinfo" is indicating CPU running at its full speed, the "CPU Freqeuncy Scaling Monitor" on the Gnome Panel says the CPU is indeed running at 1Ghz, rather then 1.8Ghz. 
But when I run "glxgears", shouldn't the frequency shoot up to 1.8Ghz? It's kinda worrysome because the value on the CPU Freqeuncy Scaling Monitor remains constant (1Ghz).

---

### Post by ubuntme on 2005-08-31
hmmm, how long do you have the cpu at 100% for? there may be a lag in either cool'n'quiet of the refresh on the system monitor.  Try restarting the system monitor?

Otherwise another program is emifreq though I have never used it.

---

### Post by Adam Lee on 2005-08-31
[QUOTE=ubuntme]hmmm, how long do you have the cpu at 100% for? there may be a lag in either cool'n'quiet of the refresh on the system monitor.  Try restarting the system monitor?

Otherwise another program is emifreq though I have never used it.[/QUOTE]

On "cat /proc/cpuinfo", it' was running at full speed for more than 2 hours. 
I tried to restart powernowd without any luck.
And I rebooted my system and it seems it's working fine now. 
However, I think in a few hours it will be running at full speed as always...
How do you restart the system monitor? 
I open up the system monitor from "Applications>System Tools", but is there any other tricks?

Thank you very much Ubuntme!

---

