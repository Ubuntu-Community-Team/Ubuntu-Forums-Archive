---
title: "Lenovo S10 con 9.10 sin wifi"
date: 2009-12-12
forum: Hardware
---

### Post by danetche on 2009-12-12
Muchachos: Soy muy feliz usuario de una Lenovo S10, y estos chiches me encantaron. Ya casi ni enciendo la pc desktop! Instale 9.10 pero no navego al no encontrar el wifi. La volvi al 9,04 y anda todo fenomeno. El JJ me fué mejor... y creo que el KK esta algo verde. 

Soy totalmente nuevo en Linux salvo algunas experiencias de hace una decada a titulo de curiosidad. Y estoy tratando de aprender no solo a usarlo, sino a comprender mejor a toda esta comunidad.

Voy a tirar un nuevo post en el temario general a ver si puedo ayudar a alguien y que alguien me ayude en algunos temas (Microfono). Slds,:D

Daniel

---

### Post by SLA_leandrin on 2009-12-12
Sería bueno que indiques que placa wi-fi tiene la lenovo a la que hacés referencia.

Te fijaste en Sistema --> Administración --> Controladores de Harware si no te sale ningún driver para instalar?

Si no te sale nada, abrí la consola en Aplicaciones --> Accesorios --> Terminal y escribí:

```
lshw
```

Y mandanos el resultado que devuelve ese comando.

Saludos.

---

### Post by danetche on 2009-12-17
> **SLA_leandrin said:**
> Sería bueno que indiques que placa wi-fi tiene la lenovo a la que hacés referencia.

Te fijaste en Sistema --> Administración --> Controladores de Harware si no te sale ningún driver para instalar?

Si no te sale nada, abrí la consola en Aplicaciones --> Accesorios --> Terminal y escribí:

```
lshw
```

Y mandanos el resultado que devuelve ese comando.

Saludos.
grcs por la resp., hoy la chiquita esta en Service xq se le "fue" la antena de WiFi interna, mañana cuando la tenga te cuento.
Slds,
Daniel

---

### Post by z37a on 2009-12-19
Mira te comento que la S10 es 100% compatible con Ubuntu netbook remix 9.10, te lo digo por experiencia propia ya que participe en el armado de una masterizacion con dual boot para esas netbooks(Si se aprueba el proyecto se va a instalar así miles de netbooks de estas). Asi que tene la tranquilidad de saber que es compatible y que si tenes un problema es por algun defecto de hardware seguramente.

---

### Post by danetche on 2009-12-20
> **z37a said:**
> Mira te comento que la S10 es 100% compatible con Ubuntu netbook remix 9.10, te lo digo por experiencia propia ya que participe en el armado de una masterizacion con dual boot para esas netbooks(Si se aprueba el proyecto se va a instalar así miles de netbooks de estas). Asi que tene la tranquilidad de saber que es compatible y que si tenes un problema es por algun defecto de hardware seguramente.
**Man, si sos aunque sea parte culpable de la config. de esta lENOVO, TE QUIERO AGRADECER, el Remix anda Super-Jamon...!!! Y a Leandrin le pego acá la lectura del comando q pidio:**

[COLOR="DarkGreen"]susana@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
PCI (sysfs)  
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 993MiB
     *-cpu
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
[/COLOR]

---

### Post by danetche on 2009-12-20
Lea: aca te mando la resolucion del comando:

  [COLOR="DarkGreen"] *-cpu
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0500000-f057ffff ioport:1800(size=8) memory:d0000000-dfffffff(prefetchable) memory:f0600000-f063ffff
[/COLOR]

---

### Post by z37a on 2009-12-20
> **danetche said:**
> **Man, si sos aunque sea parte culpable de la config. de esta lENOVO, TE QUIERO AGRADECER, el Remix anda Super-Jamon...!!! Y a Leandrin le pego acá la lectura del comando q pidio:**


Yo solo instale un UNR en una S10 y la prepare para poder ser replicada fácilmente, nada mas, el resto es cosa de Lenovo y de Canonical, no tengo nada que ver con Canonical, solo en una ínfima parte con Lenovo.

---

### Post by SLA_leandrin on 2009-12-21
Che pero al final, te anda la placa wifi o no?

---

### Post by danetche on 2009-12-21
> **SLA_leandrin said:**
> Che pero al final, te anda la placa wifi o no?

Lea: Lleve la Lenovo al service por eso, y no anda (segun el service) la etapa wi-fi del mother, y mandaron a pedir uno. Tarda 10 dias.
En el interin, me voy a Mdel Plata y la llevo, porque con una antena externa Micronet q tengo, anda al pelo, y cuando vuelva, la llevare. 

Me inquieta si con el cambio se desconfigura alguna cosa (nunca cambien un mother, y me dicen q queda todo igual) ya que anda hasta el sonido en Skype!. 

Muchas grcs por el acompañamiento en Linux, me han hecho sentir bárbaro.

Y en la desktop aun no pude resolver el tema de la fresolucion ni el sonido en skype. Pero lo dejo para luego de las fiestas

Felicidades a La Comunidad!!!

---

### Post by z37a on 2009-12-22
> **danetche said:**
> Lea: Lleve la Lenovo al service por eso, y no anda (segun el service) la etapa wi-fi del mother, y mandaron a pedir uno. Tarda 10 dias.
En el interin, me voy a Mdel Plata y la llevo, porque con una antena externa Micronet q tengo, anda al pelo, y cuando vuelva, la llevare. 

Me inquieta si con el cambio se desconfigura alguna cosa (nunca cambien un mother, y me dicen q queda todo igual) ya que anda hasta el sonido en Skype!. 

Muchas grcs por el acompañamiento en Linux, me han hecho sentir bárbaro.

Y en la desktop aun no pude resolver el tema de la fresolucion ni el sonido en skype. Pero lo dejo para luego de las fiestas

Felicidades a La Comunidad!!!

Con Linux al cambiar mother no va a pasar nada, es mas no te va a salir ni un cartelito!!!! Con la ventanita(Windows) si tendiras problemas(BlueScreens tras otro, o hardware nuevo encontrado y pedido de drivers).

---

