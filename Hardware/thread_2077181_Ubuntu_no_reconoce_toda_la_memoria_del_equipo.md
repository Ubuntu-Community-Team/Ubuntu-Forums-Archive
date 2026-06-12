---
title: "Ubuntu no reconoce toda la memoria del equipo"
date: 2012-10-27
forum: Hardware
---

### Post by fmsismo on 2012-10-27
Hola me compre y me encontré con un problema.  Ubuntu no me reconoce los 16 gb de ram que tengo instalados (puestos según el manual para que funcionen en dual channel).  

A alguno le paso esto?


Les paso lo que pude hacer de debug!

cat /proc/meminfo
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
        *-bank:1
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
             size: 8GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber2
             vendor: A1_Manufacturer2
             physical id: 2
             serial: A1_SerNum2
             slot: A1_DIMM2
        *-bank:3
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: Array1_PartNumber3
             vendor: A1_Manufacturer3
             physical id: 3
             serial: A1_SerNum3
             slot: A1_DIMM3
             size: 8GiB
             width: 64 bits
             clock: 667MHz (1.5ns)


cat /proc/meminfo 
MemTotal:        8148280 kB

uname -a -> Linux alphaprime 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Saludos y gracias.

---

### Post by guillermolisi on 2012-10-27
Si, con una placas Intel y memoria Kingston y/o Corsair DDR2 funcionando en DualChannel tuvimos que duplicar la cantidad de memoria fisica para lograr el neto requerido.

Con otras placas Intel, Asus y Gigabyte, la misma memoria funcionando tambien en DualChannel no sucedia lo mismo.

Si bien en la documentacion de esas placas Intel no habia mencion alguna a este comportamiento, con las pruebas que se realizaron quedo visto que ese reultado tenia que ver con la placa/BIOS/Controlador de memoria RAM, no con los bancos de memoria.

---

### Post by fmsismo on 2012-10-27
Hola Guille es con Kingston pero con AMD, es micro AMD con chipset AMD.  Si la sacabas de dualchannel veían todo en tus pruebas?

---

### Post by guillermolisi on 2012-10-27
Los casos que comente sinteticamente eran con procesador Intel, pero no creo que pase por ahi el tema.

Hicimos pruebas para verificar si habia alguna cuestion con las placas de memoria y las probamos en SingleChannel y en forma separada, una por una.
En ambos casos reconocia el total de la RAM instalada. La reduccion a la mitad se producia unicamente cuando se activaba el DualChannel.

---

