---
title: "Procesadores en 10.04"
date: 2010-05-26
forum: Hardware
---

### Post by Criminel on 2010-05-26
Hola,
tengo un AMD que corre a 2.2 GHz pero cuyo modelo se lista como desconocido por las herramientas de análisis de hardware y sistema de ubuntu.
El tema es que no estoy seguro de si es o no un procesador de 64bits, y la versión de ubuntu que corro es la de 32 bits.
¿Cómo puedo asegurarme de qué tipo de procesador es? y - en tal caso - ¿hay forma de actualizar el sistema operativo a 64 bits sin volver a hacer una instlación limpia?

Gracias.

---

### Post by guillermolisi on 2010-05-26
En una terminal/consola ingresa ```
sudo lshw
```y tendrias que ver una larga lista de los componentes de tu maquina.

La seccion que te interesa te deberia dar algo similar a lo que muestro a continuacion donde marco en color el dato clave de tu duda:
> *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U10
          size: 1GHz
          capacity: 1833MHz
          [COLOR=Lime]width: 32 bits[/COLOR]
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm cpufreq
          configuration: id=0

Como tu CPU posee mas de un nucleo, tambien veras algo asi donde en color te indico lo importante que tenes que observar:
> *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
            [COLOR=Lime] width: 32 bits[/COLOR]
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             [COLOR=Lime]width: 32 bits[/COLOR]
             capabilities: logical

---

### Post by Criminel on 2010-05-26
*-cpu
          description: CPU
          product: AMD Processor model unknown
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.15.3
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 1GHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy cpufreq

Concluyo que es un procesador de 64. Verdad?
Entonces... ¿qué debería hacer con la versión de ubuntu?

---

### Post by guillermolisi on 2010-05-26
Podes usar la version de 32 o la de 64 bits ya que efectivamente es de 64 bits.

Ahora, si no tenes mas de 3Gb RAM mi recomendacion es que uses 32 bits.

Por que ? Porque los sistemas de 64 bits consumen un poco mas de memoria ya que todo su sistema de punteros para direccionar datos en la RAM necesita de mas espacio que los de 32 bits. Puesto de otra forma, una instruccion completa de un procesador de 64 bits es mas grande que una de 32, por lo tanto "ocupa" mas memoria.

Pero esto es hilando finito, bien en detalle.

---

### Post by Criminel on 2010-05-26
Entiendo. El paso lógico de upgrade entonces sería ampliar la RAM.

Muchas gracias.

---

