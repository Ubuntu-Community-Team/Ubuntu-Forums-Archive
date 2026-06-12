---
title: "hay limite de ram?"
date: 2011-02-03
forum: Hardware
---

### Post by joseluis on 2011-02-03
hola amigos
recientemente me comentaron que win7 no acepta más de cuatro giga de ram en la versiones de 32 bits. Mas allá de que no se cuánto hay de cierto en esto, quisiera saber si ubuntu tiene alguna limitacion de ram en versiones de 32 o 64 bit.
Quiero comprar una nueva maquina y querria ponerle al menos 4 gigas de ram.
gracias

---

### Post by hectorivand on 2011-02-03
> **joseluis said:**
> hola amigos
recientemente me comentaron que win7 no acepta más de cuatro giga de ram en la versiones de 32 bits. Mas allá de que no se cuánto hay de cierto en esto, quisiera saber si ubuntu tiene alguna limitacion de ram en versiones de 32 o 64 bit.
Quiero comprar una nueva maquina y querria ponerle al menos 4 gigas de ram.
gracias

Hola Jose Luis, la limitación básicamente no es del sistema, si lo es de la arquitectura.

Tanto como Windows y Ubuntu (Sin PAE) de 32 Bits reconocen 4GB de Ram. La versiones de ambos sistemas de 64 Bits soportan más, para que te des una idea, Windows 7 Home Premium soporta 16Gb de ram y últimate 192gb.

En el caso de Ubuntu de 64 Bits soporta hasta 1TB.

Saludos
Nacho

---

### Post by joseluis on 2011-02-03
Bien...entendí. GRACIAS!!
pregunta final: ¿estaría bien poner 4 gigas entonces a una maquina con ubuntu de 32 entonces? los reconoce todos? porque en el caso de Win7 solo usaria 3.2 gigas. Ubuntu usaria todo?
gracias

---

### Post by hectorivand on 2011-02-03
> **joseluis said:**
> Bien...entendí. GRACIAS!!
pregunta final: ¿estaría bien poner 4 gigas entonces a una maquina con ubuntu de 32 entonces? los reconoce todos? porque en el caso de Win7 solo usaria 3.2 gigas. Ubuntu usaria todo?
gracias

Debería, pero he leído de casos que no lo toma todo. Si no te llega a tomar toda la memoria leete esto.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Saludos
Nacho

---

### Post by guillermolisi on 2011-02-03
La arquitectura IA-32, usada por todas las maquinas x86 y amd64, reserva una parte de la RAM para remapear direcciones por encima de los 3Gb para perifericos de 32 bits (que de otro modo no las verian). Por lo tanto de minima hay un costo de 64Mb RAM que es el tamaño mas pequeño reservado para esto.
Esta arquitectura, obsoleta para mi gusto, se mantiene para garantizar retrocompatibilidad.

Tambien juega mucho que tipo de hardware y que BIOS tenga la maquina en cuestion. Si el hardware esta bien preparado, con todo lo necesario para trabajar bien en 64bits con RAM >4Gb y el BIOS no lo aprovecha, estas en problemas ya que a veces ni podes actualizar el BIOS.

Ubuntu 32bits solo podra direccionar por encima de los 3Gb RAM si y solo si usa el kernel PAE, sino pasara mas o menos lo que sucede con Win7 y otros SOs de 32 bits.

---

### Post by juancarlospaco on 2011-02-03
Ademas de lo que dice Guillermo, 
no se gasten demasiado en tanta RAM que el cuello de botella esta en otros lados,
 ej. el Disco de platos Mecanico

---

### Post by MeduZa on 2011-02-03
hola, te comento, tengo ubuntu 10.10 32bits, y tengo 4gb de ram, debido a que el CPU en 32bits solo puede manejar 3.2gb active el PAE del CPU y ahora usa 3.9gb, funciona de 10 siempre que no uses aplicaciones que necesiten mas de 4gb de ram para funcionar (lo que nunca probé)
con el PAE activado podes usar hasta 64gb en un sistema 32bits.

---

### Post by MeduZa on 2011-02-03
> **juancarlospaco said:**
> Ademas de lo que dice Guillermo, 
no se gasten demasiado en tanta RAM que el cuello de botella esta en otros lados,
 ej. el Disco de platos Mecanico

si necesitas trabajar intensivamente sobre el disco podes crear un disco en RAM eh ir copiando (sincronizando) los archivos cada X tiempo, eso no solo generaría una mejora de performance, sino que desgasta menos el disco, el único problema es que estarías trabajando sobre el aire por momentos y si es información valiosa se podría perder.

---

### Post by joseluis on 2011-02-03
bien...QUE BUENO PREGUNTAR ACÁ!!!
la cosa en cuestión es que tengo una amd64 3000+ con 2 giga de ram y pensaba meter dos gigas mas, para tener 4 gigas. La intención es trabajar con pequeños videos HD para cursos de capacitación. Tengo ubuntu 10.04 de 64 entonces ahi si que podria meter mas megas y me los aprovecharia. De todos modos como tambien tengo en otro disco win7 no me importa que me tome 3,2 en lugar de los 4. ¿está bien mi posición? Es recomendable mantener ubuntu de 64 cuando desde la misma pagina de ubuntu dice que no se recomiendo de 64? Yo tengo de 64, me anda muy bien, y no tuve problemas.Por eso , si le meto dos gigas mas creo que está bien mi reflexión?

---

