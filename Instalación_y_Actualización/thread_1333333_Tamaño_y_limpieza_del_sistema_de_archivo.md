---
title: "Tamaño y limpieza del sistema de archivo"
date: 2009-11-21
forum: Instalación y Actualización
---

### Post by aribet on 2009-11-21
Hola!
¿Cuánto debe pesar (mas menos) el sistema de archivo?

lo que me pasa es que luego de una actualización a karmic con un cd alternate, veo que mi sistema de archivos ocupó casi todo los 12 Gigas que le tengo asignado, lo cual creo que es mucho (mi home está en otra partición).

Desinstalé los programas y juegos que no uso, usé ubuntu tweak para limpiar paquetes innecesarios, eliminé lenguajes con localepurge, aun así liberé solamente como 400mb.

Mi consulta es cómo puedo optimizar el espacio, que carpetas tengo que revisar para liberar espacios o que otros elementos puedo eliminar.

Saludos y gracias de antemano

---

### Post by moreback on 2009-11-21
Creo que el caché de apt está ocupando todo tu disco /, además creo que ahí tienes todos los updates hechos durante el tiempo que usaste la 9.04 junto con los paquetes nuevos del Alternate CD.

Este caché se borra con el comando:

```
sudo apt-get clean
```

Cuéntanos cómo te va con este comando.

Saludos.

---

### Post by aribet on 2009-11-21
nada, creo que esas cosas las borré con ubuntu tweak.

---

### Post by Carlos C on 2009-11-21
Tengo mis dudas sobre lo que ocurrió cuando instalaste. Por favor escribe en el terminal:

```
sudo fdisk -l
```

y copia acá lo que te sale.

Saludos.

---

### Post by aribet on 2009-11-21
> **Carlos C said:**
> Tengo mis dudas sobre lo que ocurrió cuando instalaste. Por favor escribe en el terminal:

```
sudo fdisk -l
```

y copia acá lo que te sale.

Saludos.

```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x08000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5905    47431881    7  HPFS/NTFS
/dev/sda2            5906        6224     2562367+  82  Linux swap / Solaris
/dev/sda3            6225        7244     8193150   83  Linux
/dev/sda4            7245        9729    19960762+  83  Linux
xxxxxxxx:~$ 
```

---

### Post by moreback on 2009-11-22
> **aribet said:**
> nada,** creo **que esas cosas las borré con ubuntu tweak.

¿Revisaste que había en el directorio **/var/cache/apt/archives** ? con el comando que te di se borran todos los .deb que hay ahí.

De todas formas puedes revisar tu disco duro con **Aplicaciones -> Accesorios -> Analizador de uso de disco** y hacer que te explore el sistema de archivos, con esto verás gráficamente qué directorios están ocupando más espacio en tu disco.

Saludos-

---

### Post by aribet on 2009-11-23
> **moreback said:**
> ¿Revisaste que había en el directorio **/var/cache/apt/archives** ? con el comando que te di se borran todos los .deb que hay ahí.

De todas formas puedes revisar tu disco duro con **Aplicaciones -> Accesorios -> Analizador de uso de disco** y hacer que te explore el sistema de archivos, con esto verás gráficamente qué directorios están ocupando más espacio en tu disco.

Saludos-

si, ya estan borrados. cuando los borré pesaban como 300 megas.

en el analizador de discos lo que mas pesa es la carpeta media (montado disco de windows xp) y el home (separado en otra particion) pero no me cuadran las sumas, mi disco en total es de ochenta gigas.

[IMG]http://picasaweb.google.com/lh/photo/rTc5uIBY9QR4iYjSLEDuTA?feat=directlink[/IMG]

---

### Post by moreback on 2009-11-24
por tu fdisk -l puedo calcular que tienes lo siguiente

```
 [B]7,8  GiB disco /
19,0  GiB disco /home
 2,44 GiB de Swap[/B]
```Con lo cual no veo de dónde sacas que te ocupó casi los 12GB que le asignaste al sistema de archivos.

El uso actual de las particiones las puedes ver con el comando **df -h** o con **Sistema -> Administración -> Monitor del sistema**.

¿Qué tal si pegas la salida del comando **df -h**?

Saludos.

---

