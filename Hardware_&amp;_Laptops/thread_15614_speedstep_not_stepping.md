---
title: "speedstep not stepping?"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by blah09 on 2005-02-15
ok i have an intel centrino laptop that is supposed to be running somewhere between 600mhz and 1.3ghz, but its stuck at 600mhz now for some reason... at startup it runs at 1.3ghz, then it steps down at idle, and never steps up again, even when compiling a kernel...
has this ever happened to anyone or does anyone know how i can fix this?

my cat /proc/cpufreq gives this output:
# cat /proc/cpufreq
          minimum CPU frequency  -  maximum CPU frequency  -  policy
CPU  0       600000 kHz ( 46 %)  -     600000 kHz ( 46 %)  -  userspace

and my cpuinfo give this:
# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1300MHz
stepping        : 5
cpu MHz         : 597.620
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 1183.42


any help would be appreciated :)

---

### Post by blackomegax on 2005-02-16
my 1.3 banias works fine. (except that it has the odd problem of scaling down too slow, even tho it scales up instantly when needed)

the proc info is wrong, and is why its not stepping. it thinks its max is 600mhz.

get rid of whatever ubuntu warty uses for cpu scaling and try cpufreqd, etc.

---

### Post by Strider on 2005-02-16
blah09,
I had a similar problem where the applet monitoring the speed would be 0, 137, or 10xx.  I found out that I needed to specify the "speedstep-centrino" module in the /etc/module file.  After that it scaled down properly.  At idle it's at 600MHz and it goes up depending on what I'm doing on the system.

Hope that helps.

---

### Post by blackomegax on 2005-02-16
i found it


# sudo echo -n "1300000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq

that SHOULD fix it.

---

### Post by Snover on 2005-09-12
[QUOTE=blackomegax]i found it


# sudo echo -n "1300000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq

that SHOULD fix it.[/QUOTE]
 Sorry for bringing up an old thread, but I am having a similar issue. I have tried "modprobe speedstep-centrino", but that didn't do anything. I then tried echoing "1400000" (I have a 1400MHz processor) to /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq, but it is still stuck at 600000. When turned on while plugged in, it seems to operate OK.

# uname -a
Linux northstar 2.6.10-5-686 #1 Thu Aug 18 22:39:14 UTC 2005 i686 GNU/Linux

# cat /proc/cpufreq
          minimum CPU frequency  -  maximum CPU frequency  -  policy
CPU  0       600000 kHz ( 42 %)  -     600000 kHz ( 42 %)  -  performance

# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1400MHz
stepping        : 5
cpu MHz         : 597.616
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 1183.74

---

### Post by webber on 2005-09-25
I encountered the same problem. My amilo is powered by dothan 1,5 and when I first installed ubuntu speedstep didn't work at all. So I added p4-clockmod to /etc/modules and now it is actually working but from 75 up to 600MHz, I can scale it by echoing desired speed (up to 600MHz) to /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  but when I try to do it with scaling_max_freq everything seems to be ok but 600MHz is as high as it really gets. I tried to edit these files manually but like Snover mentioned above it remains untouched. Any help would be apreciated :)

---

### Post by CDrewing on 2007-10-31
And now it's me bringing up this old thread. I have a  Intel(R) Pentium(R) 4 CPU 2.60GHz
and the speedstep seems not to work.

> root@ubuntu:/proc# cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.60GHz
stepping        : 9
cpu MHz         : 2600.237
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5204.48
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.60GHz
stepping        : 9
cpu MHz         : 2600.237
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5200.59
clflush size    : 64


Can anybody help?

Kind regards,
Christian.

---

