---
title: "Cpufreq not working"
date: 2009-01-06
forum: Hardware
---

### Post by vishnumrao on 2009-01-06
Urgent Help needed!

I was playing around with my bios and came across some jumper free overclocking options in the bios. I set it to overclock by 1% and booted into my Intrepid install. As soon as I was logged into Gnome, I get this error(or rather warning) message as shown in the attached screenshot.

Problem: The CPU is stuck at 2.01 GHz and does not do dynamic scaling under low load. Its stuck at max speed. I have brought the bios to default settings (even tried resetting the bios battery, I knew it would not help.). I also tried the xfix option in the recovery mode.

cat /proc/cpuinfo yields: 
```

vishnumrao@vishnumrao-desktop:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 12
model name	: AMD Athlon(tm) 64 Processor 3000+
stepping	: 0
cpu MHz		: 2009.774
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up
bogomips	: 4019.54
clflush size	: 64
power management: ts fid vid ttp

```

Can someone please suggest a fix.

Thanks in advance.
Vishnu Rao.

---

### Post by vishnumrao on 2009-01-06
Update: I don't know if its a software issue. I feel it could be a hardware problem. Tried booting up with Ubuntu Intrepid live cd and a Xubuntu 8.04 live cd. cpuinfo shows same results as above. 

I know this is a wrong place to ask this question, does anyone know how any tools to check cpufreq? I am going to try UBCD. What could have gone wrong with the hardware?

---

