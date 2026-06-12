---
title: "here is my cpu info, sth is missing, why?"
date: 2009-08-05
forum: Hardware
---

### Post by say2sky on 2009-08-05
cpu U2400, chipset 945GM

> uname -a
Linux ubuntu2 2.6.24-24-generic #1 SMP Fri Jul 24 22:46:06 UTC 2009 i686 GNU/Linux
You have new mail in /var/mail/root


>      *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) Duo CPU      U2400  @ 1.06GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          slot: CPU 1
          size: 1066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr
          configuration: id=0


I can find neither cpufreq nor ssse3.
frequency scaling is not working.

> sudo /etc/init.d/powernowd start
 * Starting powernowd...                                                                            * CPU frequency scaling not supported... 

---

### Post by aesis05401 on 2009-08-05
Hello, 

I don't have the answer to all of your issues, but the error message you receive from powernow appears to be widespread:[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/44699]("https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/44699")

If you read the linked thread you will see people reporting the same error with both modern and legacy chips.

---

