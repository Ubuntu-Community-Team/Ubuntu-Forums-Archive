---
title: "¿procesador de 32 ó 64 bit?"
date: 2009-11-18
forum: Instalación y Actualización
---

### Post by asterix77 on 2009-11-18
Tengo una gran duda con mi pc. Tiene pegado en el frente el logo del procesador AMD el cual tiene en la esquina inferior derecha el número 64. Asumo que es porque es de 64 bit. 
Hace ya varios meses atrás le instalé ubuntu 9.04, para lo cual baje la distro de 64 bit. Luego de quemarla, la hice correr, pero no pude llegar al entorno gráfico, ni siquiera a la terminal. Quemé varias veces la iso, inclusive a la mínima velocidad, pero todo fue igual. 
Mi solución fue de descargar la versión de 32 bit, la cual corrió a la perfección a la primera, y que posteriormente instalé.

Ahora quiero cambiarme a Jaunty, pero si mi procesador es de 64 bit quiero bajar esa versión. ¿Existe alguna forma de saber a través de la terminal u otra forma si realmente mi procesador AMD es de 64 bit?

Saludos

---

### Post by nopersona on 2009-11-18
Para ver las caracteristicas de tu procesador abre un terminal y pega

```
cat /proc/cpuinfo
```

Si es de 64 bit no debería haber problemas. Tampoco estaría mal la información de tu hardware.

---

### Post by asterix77 on 2009-11-19
He aquí lo que lista cat:


cat /proc/cpuinfo

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) Dual Core Processor 4050e
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2008.90
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) Dual Core Processor 4050e
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2008.90
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

---

### Post by Carlos C on 2009-11-20
También se puede ver con el comando:
```
sudo lshw -C cpu
```

---

