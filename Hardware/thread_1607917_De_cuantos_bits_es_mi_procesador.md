---
title: "De cuantos bits es mi procesador?"
date: 2010-10-28
forum: Hardware
---

### Post by pinguinosaurio on 2010-10-28
Que tal, he tenido una duda desde hace tiempo, resulta que cuando compré mi notebook emachines e625, en la informacion que trae pegada en su superficie, que te dice sus caracteristicas, decia que tiene un AMD Athlon 64 TF-20, la raja dije yo, pero cuando probé con el Ubuntu en el monitor del sistema dice que es AMD Athlon(tm) Processor TF-20, pero no tiene el numero 64, estuve buscando por internet este modelo de procesador, pero la mayoria apuntaban solo al AMD 64 Athlon TF-20, y no al que me dice ubuntu, entonces u&#347;e el comando 

cat /proc/cpuinfo

Y me salio esto, alguien me prodria explicar si el procesador es de 32 bits o 64 bits?

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 124
model name    : AMD Athlon(tm) Processor TF-20
stepping    : 2
cpu MHz        : 800.000
cache size    : 512 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips    : 1595.98
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

Y con el comando sudo lshw

ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Notebook
    product: eMachines E625
    vendor: eMachines
    version: V1.11
    serial: LXN290R01793633B881601
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=notebook uuid=38383939-3338-3335-3635-002622223FCF
  *-core
       description: Motherboard
       product: HM50-YK
       vendor: eMachines
       physical id: 0
       version: N/A
       serial: LXN290R01793633B881601
     *-firmware
          description: BIOS
          vendor: eMachines
          physical id: 0
          version: V1.11 (06/03/2009)
          size: 114KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor TF-20
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: Engineering Samplenology
          slot: Socket M2/S1G1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back

Otra cosa que encontré en un foro de Debian es lo siguiente:

Una forma rápida de salir de dudas es intentar arrancar el equipo con  el cd de instalación de Lenny para amd64, te puedes bajar el net  install que ocupa muy poco, lo metes y si tu procesador no soporta  64bits se parará la carga indicándote que ese kernel no funcionará en tu  máquina.


Dicho y hecho, me descargué la version de Ubuntu amd64 (usaba la version 1386 con anterioridad) y el pc inicio el livecd sin problemas, de hecho este post lo escribo usando Ubuntu con amd64, los comados los ejecute en ubuntu amd64.



Es verdad que si mi procesador fuera solo de 32 bits no hubiese iniciado la version de Ubuntu para arquitecturas de 64 bits?


Si mi procesador fuese en el evento de 64 bits, quiere decir que debo usar la version amd64 para sacarle mas partido?


Gracias, ojala me saquen de esta duda


Hasta la proxima

---

### Post by Wiredfixer on 2010-10-28
Tal vez debiste empezar con Google:

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20TF-20%20-%20AMGTF20HAX4DN.html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20TF-20%20-%20AMGTF20HAX4DN.html)

Tu procesador, en efecto, es de 64 Bits.

De hecho, ya la gran mayoria de los procesadores de esta epoca manejan los 64 Bits, algunos sistemas operativos no estan aptos para su uso, asi que pueden manejarse dentro de un entorno de 32bit.

Y Si, la instalacion no hubiera ocurrido.

Te recomiendo que siempre visites la pagina del fabricante, ahi siempre hay informacion de lo que necesites.

---

### Post by pinguinosaurio on 2010-10-28
Gracias por responder tan rapido amigo, en efecto busque en google y me llevo exactamente a esa pagina, el problema es que Ubuntu no me colocaba el bendito 64, por eso pensaba que era quiza otro modelo de procesado, la verdad que no soy muy entendido en esta clase de asuntos, por ello recurri al foro.

Entonces tu me recomendarias que instale la version amd64 de Ubuntu? es cierto que se grana mayor aprovechamiento del procesador?

De antemano gracias

---

### Post by bichopro on 2010-10-28
En un terminal:

> sudo lshw

El resultado sale en la linea 7 u 8:

> width: XX bits

Donde XX es tu arquitectura

---

### Post by asterix77 on 2010-10-29
Bueno, mi notebook venia con un procesador AMD, pero en ninguna parte decía que era de 64, ni siquiera en el logo del procesador, por lo que en primera instancia le instalé sino mal no recuerdo una version de ubuntu 8.10 de 32. Fue sino hasta la versión 9.04 que corriendo el comando "sudo lshw" y observando que en "width" me aparecía "64 bits" que me dí cuenta de ello. Por lo que probé el live cd de 64 bit, y oh para mi sorpresa corrió en forma sorprendente.
 
 
Saludos

---

