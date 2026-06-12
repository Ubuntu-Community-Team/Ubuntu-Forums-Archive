---
title: "Particiones no reconocidas"
date: 2009-08-14
forum: Instalación y Actualización
---

### Post by 3nG3ndR0 on 2009-08-14
hola amigos quise reinstalar ubuntu, pero me tope que no me reconoce las particiones el instalador ni gparted pero si el sistema, que sera como solucionar eso.


adjunto una imagen para que este mas claro.

---

### Post by Patriciologico on 2009-08-14
Que extraño...Probaste otro disco de instalacion? ¿montando las particiones con mount previamente? ¿en que sistema de ficheros estan tus particiones?

Segun el pantallazo veo que tu dvd es 9.04 ¿efectivamente es asi?

Saludos!

---

### Post by 3nG3ndR0 on 2009-08-14
> **Patriciologico said:**
> Que extraño...Probaste otro disco de instalacion? ¿montando las particiones con mount previamente? ¿en que sistema de ficheros estan tus particiones?

Segun el pantallazo veo que tu dvd es 9.04 ¿efectivamente es asi?

Saludos!

1.- Si probé con otros disco de instalacion 9.04, 8.10 y me dice que hay sistema instalado, pero tengo instalado ubuntu 9.04 y win. vista. tambien probé con el dvd de win. vista y este si me muestra las particiones.

2.- En el disco de instalación de ubuntu puedo montar la particiones.

3.- ext4 y nfts.

---

### Post by AlexDDR on 2009-08-15
pincha en gparted con el boton derecho y elige "informacion" y ve que estado tiene

lo mas probable es que tengas medio dañada o tenga conflictos entre los datos (inico y fin) de las particiones y por eso es que gparted no la lee bien ni deja que la toques (es por seguridad). para arreglarla la tabla de particiones y para arreglarla hay un programa disponible para varios sistemas operativos incluido linux llamado TESTDISK y se encuentra en los repositorios de ubuntu

asi que basta con el comando 

sudo apt-get install testdisk


posterior a eso debes ejecutar testdisk en la consola e ir navegado en su interfaz en modo texto  para volver a escribir la tabla de particiones nuevamente

yo he tenido que hacer este procedimiento cuando formateo completamente un disco con gparted haciendo todas las particiones, incluidas las de windows y luego instalo windows, pero el particionador de windows me hecha a perder todo, por lo que recomiendo inicializar el disco en windows y crear las particiones de windows desde el disco de instalacion del mismo (esto me ha pasado 2 veces ya)


te dejo la guia que me sirvio a mi

[http://www.eqsoft.net/blog/index.php?/archives/36-Recuperando-tabla-de-particiones-con-Testdisk.html](http://www.eqsoft.net/blog/index.php?/archives/36-Recuperando-tabla-de-particiones-con-Testdisk.html)


de cualquier manera puedes solo escanear las particioes a ver si el programa detecta algun problema si es que no quiere tcar el disco todavia para RESPALDAR TODOS TUS DATOS!!!


saludos

---

### Post by jjgomera on 2009-08-15
Es raro porque según la captura parece que nautilus si las reconoce, ¿las puedes montar con normalidad en el liveCD?

Prueba a lanzar gparted desde una terminal a ver si da algún fallo.

Prueba también una vez abierto gparted en el menu gparted/monstrar caracteristicas si tienes la opción para ext4 y ntfs y tienen activada al menos la opción de detectar

¿Y un sudo fdisk -l que te devuelve?

---

### Post by orlox on 2009-08-15
Es extraño tambien que la suma de los tamaños de las particiones sean muy distintos al espacop total sin asignar...

---

### Post by AlexDDR on 2009-08-15
Por eso es lo que digo qu elo mas probable es que sea un error en la tabla de particiones, en la que el fin de una puede estar sobreescribiendo el comienzo de otra, talvez el sistema la monta pero eso no garantiza que haya problemas al llenarlas y los datos de uno pisen a la otra.

Lo mejor es ejecutar testdisk y salir de las dudas.

---

### Post by 3nG3ndR0 on 2009-08-17
> **AlexDDR said:**
> pincha en gparted con el boton derecho y elige "informacion" y ve que estado tiene

lo mas probable es que tengas medio dañada o tenga conflictos entre los datos (inico y fin) de las particiones y por eso es que gparted no la lee bien ni deja que la toques (es por seguridad). para arreglarla la tabla de particiones y para arreglarla hay un programa disponible para varios sistemas operativos incluido linux llamado TESTDISK y se encuentra en los repositorios de ubuntu

asi que basta con el comando 

sudo apt-get install testdisk


posterior a eso debes ejecutar testdisk en la consola e ir navegado en su interfaz en modo texto  para volver a escribir la tabla de particiones nuevamente

yo he tenido que hacer este procedimiento cuando formateo completamente un disco con gparted haciendo todas las particiones, incluidas las de windows y luego instalo windows, pero el particionador de windows me hecha a perder todo, por lo que recomiendo inicializar el disco en windows y crear las particiones de windows desde el disco de instalacion del mismo (esto me ha pasado 2 veces ya)


te dejo la guia que me sirvio a mi

[http://www.eqsoft.net/blog/index.php?/archives/36-Recuperando-tabla-de-particiones-con-Testdisk.html](http://www.eqsoft.net/blog/index.php?/archives/36-Recuperando-tabla-de-particiones-con-Testdisk.html)


de cualquier manera puedes solo escanear las particioes a ver si el programa detecta algun problema si es que no quiere tcar el disco todavia para RESPALDAR TODOS TUS DATOS!!!


saludos

hola parece que tienes razón me devuelve esto:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  7821 254 63  125660367
 2 E extended              7822   0  1 19456 254 63  186916275
 3 P HPFS - NTFS          14221   0  1 19456 254 63   84116340
**Space conflict between the following two partitions**
 2 E extended              7822   0  1 19456 254 63  186916275
 3 P HPFS - NTFS          14221   0  1 19456 254 63   84116340
   X extended              7822   0  2  9170 254 63   21671684
 5 L Linux                 7822   2  1  9170 254 63   21671559
   X extended              9171   0  1 14085 254 63   78959475
 6 L Linux                 9171   1  1 14085 254 63   78959412
   X extended             14086   0  1 14219 254 63    2152710
 7 L Linux Swap           14086   1  1 14219 254 63    2152647


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```

no se que hacer alguna sugerencia por favor.

---

### Post by Patriciologico on 2009-08-17
Estuve buscando informacion y llego a lo mismo que te dice Alex: reescribir tabla de particiones, que aunque puede mantener tus datos, lo mejor es respaldar antes.

---

### Post by AlexDDR on 2009-08-18
por lo menos yo cada ves que el particionador de windows me estropea la tabla de particiones , la recupero con test disk, de hecho nunca he perdido datos, ademas el programa te deja ver los datos de las particione para ver si se encuentran bien.

Lo mas complicado es entender lo que hace y que uno pierda el miedo a que va a borrar todo y tan solo re escribir la tabla con lo que te parezca mas de acuerdo con las particiones que tu creaste.

 de hecho puedes jugar un poco y una vez que arregles las particiones , gparted lo va  a leer y te permitirá volver a crearlas o modificarlarlas de manera mas facil

pero igual respalda tus datos importantes

saludos

---

