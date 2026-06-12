---
title: "Pc funcionando con un solo core del procesador"
date: 2010-03-02
forum: Hardware
---

### Post by masterl1nk on 2010-03-02
Hoy estaba agregandole unas cosas a conky y para mi sorpresa al abrir el monitor de sistema, veo un solo núcleo del procesador :/ siendo que tngo un athlon x2 5000.. recuerdo que hace un tiempo habia visto los dos cores sin problemas..

[IMG]http://i46.tinypic.com/rtmioh.jpg[/IMG]

> nico@nico-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
**cpu cores	: 1**
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2000.19
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

la salida de uname -a
> Linux nico-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

es ubuntu 9.10 de 32 bits

cpuinfo tambien dice que tengo un solo núcleo, tienen idea de como puedo arreglarlo?

gracias!

---

### Post by alfplayer on 2010-03-03
Hay unos reportes de bugs de este problema. Hay alguien que lo resolvió volviendo a como estaba la configuración ACPI del BIOS, y otro dice que lo estaba causando un hub USB.

---

### Post by mama21mama on 2010-03-05
proba encenderlo a ver como va.

> echo 1 | sudo tee /sys/devices/system/cpu/cpu1/online
[URL="http://mamalibre.eshost.com.ar/?q=node/244"]
Fuente[/URL]

---

