---
title: "¿Que me recomiendan?"
date: 2009-11-23
forum: Instalación y Actualización
---

### Post by asterix77 on 2009-11-23
Bueno ha llegado la hora de actualizarme; después de más de un año ya de usar mi notebook con intrepid de 32 bit, me he dado cuenta de que soporta 64 bit. He descargado la versión de 64 y me ha funcionado de maravillas. Hasta me ha reconocido el moden de banda ancha movil como en windows, es decir como modem y como unidad de almacenamiento.

Pero creo que cometí algunos errores al instalar intrepid; una de ellas fue el de no montar mi home en una partición aparte. Tengo mis temores, deberé respaldar todo mi home, y en el caso de mis programas y configuraciones no sé si van a seguir funcionando y en el caso de hacerlo, no sé si guardará mis configuraciones.

Quiero formatear mi disco duro a ext4, e instalar en forma limpia desde el cd, y por cierto esta vez haré una partición solo para mi home.

He aquí lo que me arroja fdisk -l

Disco /dev/sda: 60.0 GB, 60011642880 bytes
255 cabezas, 63 sectores/pista, 7296 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd8000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         138     1108453+  83  Linux
/dev/sda2             139        7296    57496635    5  Extendida
/dev/sda5             139        6998    55102918+  83  Linux
/dev/sda6            6999        7296     2393653+  82  Linux swap / Solaris

Disco /dev/sdb: 252 MB, 252968960 bytes
8 cabezas, 61 sectores/pista, 1012 cilindros
Unidades = cilindros de 488 * 512 = 249856 bytes
Identificador de disco: 0x00000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema

¿Que es lo que me recomiendan antes de actualizarme?

Saludos

---

### Post by AlexDDR on 2009-11-23
depende de que programas ocupes, si instalas muchos juegos ocuparan mas espacion, peor si no con una particion de 15gb  para raiz "/" deberia alcanzar y el resto para home


vas a respaldar  o tienes otro disco mas grande me imnagino, saludos

saludos

---

### Post by asterix77 on 2009-11-23
Primero que nada, gracias por responder.

En realidad, mi notebook lo uso solo para trabajo, navegar, etc. Nunca lo he usado para jugar, (para eso tengo una consola llamada windows ;)). Bromas aparte, tengo un disco duro portatil con capacidad suficiente para respaldar (500 gigas). Mi principal temor es el de perder mis aplicaciones ya configuradas (correos, etc).

Saludos

---

### Post by Patriciologico on 2009-12-08
Asterix, con 10 gb para tu / andaras mas que bien, en cuanto al respaldo hay varias herramientas que hacen un backup del home y luego instalas la misma herramienta en tu nueva instalacion y restaurara el home (deberas tener un usuario del mismo nombre y el mismo ID (eso facilita las cosas)

Considera lo siguiente, desde Intrepid, algunas aplicaciones han ido cambiando la ubicacion de sus ficheros de configuracion, para adaptarse al nuevo standar.

Antes lo hacian directamente en tu home, y ahora "creo" han ido pasando a .gnome2. El creo es importante por que lo lei hace tiempo y no estoy seguro, que aplicaciones y adonde llevan sus configuraciones.

Para evitarte problemas crea dos usuarios en la nueva instalacion, con superpoderes por si algo no anda bien en el antiguo usuario recurres al nuevo.

Saludos

---

