---
title: "USB Drive sin permisos"
date: 2009-07-30
forum: Hardware
---

### Post by aledruetta on 2009-07-30
¡Hola Comunidad!

Tengo un disco externo USB WD de 80 Gb. Haciendo experimentos, me metí con los permisos del disco, y ahora, un tiempo después, quiero instalar un programa que tengo ahí, en una computadora con Windows y no lo ejecuta, me dice que no tengo permisos para eso.

Los permisos de todas las carpetas y archivos quedaron así:
```
*rwxrwxrwx root root ***********
```Los * son los datos que varían de un archivo o directorio a otro.

Intenté:
```
sudo chown -R alejandro:alejandro /media/My\ Passport
```pero cuando listo con
```
ls -l
```vuelven a aparecer los permisos de la misma manera que antes.

¿Qué puede estar sucediendo?

Gracias,
Alejandro.

---

### Post by robertor on 2009-07-31
El disco duro en que esta formateado? Si lo esta con ext2, ext3 o similares, nativos de Linux, te debiera tomar esos permisos, si esta con ntfs, esos permisos no te los deberia tomar ni por si acaso.
Saludos!
Roberto

---

### Post by moreback on 2009-07-31
Tengo la impresión que el disco se está montando con alguna opción como **noexec**, lo que evita que se puedan ejecutar archivos desde esa unidad.

---

### Post by aledruetta on 2009-07-31
> **robertor said:**
> El disco duro en que esta formateado? Si lo esta con ext2, ext3 o similares, nativos de Linux, te debiera tomar esos permisos, si esta con ntfs, esos permisos no te los deberia tomar ni por si acaso.
Saludos!
Roberto

Gracias Roberto,

El disco está en formato NTFS. No sabía que estando en ese formato no aceptaba modificar los permisos.
Lo que me pregunto, entonces, es ¿porqué si siempre tuve permisos, ahora no los tengo?

---

### Post by aledruetta on 2009-07-31
> **moreback said:**
> Tengo la impresión que el disco se está montando con alguna opción como **noexec**, lo que evita que se puedan ejecutar archivos desde esa unidad.

Moreback, ¿Qué pude haber hecho para que eso suceda? Lo único que hice con el disco fue -eso creía yo- cambiar los permisos recursivamente.

---

### Post by robertor on 2009-07-31
Si haces un ```
mount
```te debiera mostrar todos los discos que tienes montados.
A mi me aparece así una partición ntfs que tengo montada:
```
/dev/sda4 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=409
```

Compara con lo que aparece a ti.
Saludos!
Roberto

---

### Post by aledruetta on 2009-07-31
Roberto, esto me informa mount:
```
/dev/sdb1 on /media/My Passport type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```Es lo mismo que en tu caso ¿Qué significa eso? ¿Se puede deducir algo de eso?

Edit: vale aclarar que así se monta en Ubuntu, pero el problema lo tengo al intentar ejecutar programas de instalación en Windows.

---

### Post by Carlos C on 2009-08-01
Puedes mirar acá:

[http://ubuntuforums.org/showthread.php?t=1217453](http://ubuntuforums.org/showthread.php?t=1217453)

Saludos.

---

### Post by aledruetta on 2009-08-01
> **Carlos C said:**
> Puedes mirar acá:

[http://ubuntuforums.org/showthread.php?t=1217453](http://ubuntuforums.org/showthread.php?t=1217453)

Saludos.

Hola Carlos C,

Estuve mirando el hilo, pero, si no entendí mal, ahí explican cómo montar una partición Windows en un equipo Ubuntu ¿es así? Puede ser que yo no esté interpretando bien la información.

Lo que me está ocurriendo es que el disco externo, que hasta hace pocos días no presentaba ningún problema en Windows, ahora (en Windows) me dice que no tengo permisos para ejecutar un instalador .exe, el setup de una aplicación (que ya la instalé mil veces en varios equipos Windows). Y eso comenzó a suceder después que estuve haciendo algunos experimentos con los permisos en ese disco, pero en Ubuntu.
```
sudo chmod 777 /My\ Passport -R
```Ahora, cuando quiero cambiar los permisos desde Ubuntu, no lo consigo. No estoy entendiendo qué sucede ¿Por qué si antes los cambió, ahora no?

¿Cómo tendrían que estar los permisos para que Windows vuelva a ejecutar programas en ese disco? ¿Cómo hago para modificar esos permisos?

Gracias por cualquier ayuda que me puedan brindar,
Alejandro.

---

### Post by moreback on 2009-08-01
> **aledruetta said:**
> Lo que me está ocurriendo es que el disco externo, que hasta hace pocos días no presentaba ningún problema en Windows, ahora (en Windows) me dice que no tengo permisos para ejecutar un instalador .exe, el setup de una aplicación (que ya la instalé mil veces en varios equipos Windows)

Ah! eso es un problema netamente de Windows, quizás haya sido causado por los comandos ejecutados en Ubuntu, pero finalmente el problema se debe resolver en Windows.

Me temo que debes pedir ayuda en un foro para Windows.

Saludos.

---

### Post by aledruetta on 2009-08-01
> **moreback said:**
> Ah! eso es un problema netamente de Windows, quizás haya sido causado por los comandos ejecutados en Ubuntu, pero finalmente el problema se debe resolver en Windows.

Me temo que debes pedir ayuda en un foro para Windows.

Saludos.

No estoy de acuerdo. El problema se originó al gestionar los permisos en Ubuntu. Y el problema persiste, porque no puedo cambiar los permisos en Ubuntu. Hace ya unos seis meses que sólo uso Ubuntu, ahora cuando vuelvo a instalar un programa en un computador que usa Windows me encuentro con que el disco USB ya no se comporta como antes. 

Imagina que alguien de Windows va a saber qué tengo que hacer con chmod, chown o fstab o lo que sea. Ellos me van a responder lo mismo, que pregunte en Ubuntu. Es como si alguien pide información para acceder desde Ubuntu a una partición Windows que se rebela y le contestan que le pregunte a Bill Gates cómo se hace eso, que la culpa la tiene Microsoft porque no libera el código de Windows.

Me gustaría descubrir qué ocurrió en Ubuntu para que esto no ocurra nuevamente. Sinceramente, creo que es un problema que tengo que resolver en Ubuntu, que es mí sistema operativo, y no en Windows. No puedo creer que Ubuntu no sirva para solucionar un problema que se originó en Ubuntu. Además, esto que me ocurrió a mí, le puede ocurrir a cualquier Ubuntero que pruebe herramientas de Ubuntu con su disco formateado en NTFS ¿A quién le van a preguntar?

---

### Post by moreback on 2009-08-01
El problema se da sólo en Windows, en Ubuntu te funciona perfectamente el disco USB, ¿no? Los usuarios de Linux no son los mismos que en Windows, por lo que el tema de permisos de usuarios debe hacerse directamente en Windows, con sus herramientas.

Si no estás de acuerdo, te invito a reportar ese bug en ntfs-3g.

Saludos.

---

### Post by aledruetta on 2009-08-02
¿Alguien sabe cómo volver atrás los permisos de ususario que fueron modificados por medio de comandos como chmod y chown, en un disco USB externo, de tal manera que este disco vuelva a ser aceptado normalmente por otros sitemas operativos? ¿Es posible, o una vez que se modificaron ya no se puede volver atrás? 
En el caso de que no fuera posible ¿sólo me queda formatear el disco? Si copio la información en el disco rígido interno, y después de formateado el disco la vuelvo a copiar al disco externo ¿Qué va a suceder con los permisos? ¿Siguen igual o van a estar nuevamente disponibles para operar en cualquier sistema operativo?

Por favor, si alguien me puede orientar, sería de gran ayuda.
Gracias,
Alejandro.

---

### Post by kornykyano on 2009-08-03
Pero que casualidad!! yo tbn estoy teniendo este problema pero con un pendrive de 1GB. No hay forma de darle permiso de escritura. Ademas alguna carpetas aparecieron diferentes archivos con letras raras por ejemplo:
[B]
file:///media/PEPE/Libros/on%20rdf:a.bou/ÿt&#9562;u%15&#9617;%03&#9619;.ÿîå[/B]

Probe con:

```
sudo chmod -Rf 777 /media/PEPE/

chmod: no se puede acceder a «/media/PEPE/.Trash-1000/ 450]/li.nea»: No existe el fichero ó directorio
```

y sigue con todos los demas de igual forma

Ni tampoco modicando las propiedades de las carpetas aún siendo root desde nautilus.

si no hay sugerencia....a formatear!

---

### Post by aledruetta on 2009-08-03
> **kornykyano said:**
> si no hay sugerencia....a formatear!

La verdad que urgencia no hay. La duda es: si formateo, guardando antes la información en el rígido interno, cuando vuelque otra vez la info en el disco externo ¿se va a solucionar el tema de los permisos? ¿o los permisos van a seguir comportándose de la misma manera?

Y ahora que lo pienso bien, el disco externo es de 180 Gb. y el interno es de 80 Gb., así que tampoco voy a poder mover la info de lado al otro. Así que lo mejor sería conseguir entender lo que está pasando y buscar alguna solución, si es que existe.

---

### Post by kornykyano on 2009-08-04
Bien, buscando me encontrado con la siguiente seudo-tuto o receta :)

Es posible que estos dispositivos al ser usado simultaneamente en windows como en linux crea algun tipo de error en la tabla de partición del mismo.
Por lo tanto haria las siguientes pruebas:

Escribir:

**tail -f /var/log/syslog**

luego conectar el dispositivo, si sale algo de "filesystem panic" se podria arreglar. Ahora desmontandolo (**umount /dev/XXX**) escribir:

**sudo dosfsck -a -v /dev/sdxx**

 donde sdxx depende de la ubicación (se puede averiguar con **fsck -l**).

Si tenes mucha suerte la habras recuperado, de lo contrario como no encontre otra solucion..... hay que formatear (no queria, pero bue!!)..

ya que estoy muestro como lo hice:

Desmontar el USB:
**umount /dev/XXX**

Formatear empleando el sistema de ficheros que usa Windows que es fat vfat:
**sudo mkfs.vfat /dev/XXX**

Montar el USB:
**mount /dev/XXX**

Tambien se podria haber elegido “mkfs.ext2“ o “mkfs.ext3” (ver en **whereis mkfs**)

y listo!...me voy a dormir 8-)

---

### Post by Carlos C on 2009-08-04
Hola. Sin haberlo probado me parece que lo que dice kornykyano tiene más lógica, es posible que haya habido un problema con la tabla de particiones. aledruetta, no puede ser un problema de permisos, simplemente porque los permisos que creas en linux un sistema operativo como windows no los reconoce, no sabe que existen.
Espero que el problema se arregle.
Saludos!

---

### Post by aledruetta on 2009-08-04
> **kornykyano said:**
> Por lo tanto haria las siguientes pruebas:

Escribir:

**tail -f /var/log/syslog**

luego conectar el dispositivo, si sale algo de "filesystem panic" se podria arreglar. Ahora desmontandolo (**umount /dev/XXX**) escribir:

**sudo dosfsck -a -v /dev/sdxx**

 donde sdxx depende de la ubicación (se puede averiguar con **fsck -l**).

Si tenes mucha suerte la habras recuperado, de lo contrario como no encontre otra solucion..... hay que formatear (no queria, pero bue!!)..

Hice lo que dijiste, me devuelve:
```
dosfsck 3.0.1 (23 Nov 2008)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 0.

```

¿Se puede interpretar algo a partir de eso?

---

### Post by aledruetta on 2009-08-04
> **Carlos C said:**
> ...me parece que lo que dice kornykyano tiene más lógica, es posible que haya habido un problema con la tabla de particiones...
Hola Carlos C,

Entonces, siguiendo por ese camino de investigación, dejo información para ver si ayuda a vislumbrar cuál puede ser el problema:

```
$df -h
/dev/sdb1             150G   75G   75G  51% /media/My Passport

$mount
/dev/sdb1 on /media/My Passport type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

$cat /etc/fstab
No aparece mención al disco.

$fdisk -l
Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8f9c798a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
```

---

### Post by kornykyano on 2009-08-05
que resultado te dio :
**tail -f /var/log/syslog**

pero despues ahi te marca el error:

[FONT="Courier New"]Currently, only 1 or 2 FATs are supported, not 0.[/FONT]

La tabla de particion esta dañada, quizas se pueda recuperar, pero ya nesecita conocimiento mucho mas técnico...algún Ingeniero por ahi!!

Para mi hay que formatear, sin embargo hay una posibilidad para juagr com **Testdisk** yo lo he utilizado alguna vez sin exito. Busca el manual y proba.

Saludos

---

### Post by Carlos C on 2009-08-05
Testdisk fue incorporado en los repositorios para Jaunty, así que no habría problema con que lo pruebes. En el wiki está la información para recuperar tu tabla de particiones:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Saludos.

---

### Post by aledruetta on 2009-08-05
> **kornykyano said:**
> que resultado te dio :
**tail -f /var/log/syslog**

El resultado fue:

```
Aug  5 18:43:38 alejandro-laptop kernel: [18988.060042] usb 1-4: new high speed USB device using ehci_hcd and address 7
Aug  5 18:43:39 alejandro-laptop kernel: [18988.214068] usb 1-4: configuration #1 chosen from 1 choice
Aug  5 18:43:39 alejandro-laptop kernel: [18988.238212] scsi7 : SCSI emulation for USB Mass Storage devices
Aug  5 18:43:39 alejandro-laptop kernel: [18988.239577] usb-storage: device found at 7
Aug  5 18:43:39 alejandro-laptop kernel: [18988.239581] usb-storage: waiting for device to settle before scanning
Aug  5 18:43:40 alejandro-laptop chipcardd[3608]: devicemanager.c: 3373: Changes in hardware list
Aug  5 18:43:44 alejandro-laptop kernel: [18993.236235] usb-storage: device scan complete
Aug  5 18:43:44 alejandro-laptop kernel: [18993.236871] scsi 7:0:0:0: Direct-Access     WD       1600BEV External 1.05 PQ: 0 ANSI: 4
Aug  5 18:43:44 alejandro-laptop kernel: [18993.276608] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Aug  5 18:43:44 alejandro-laptop kernel: [18993.277442] sd 7:0:0:0: [sdb] Write Protect is off
Aug  5 18:43:44 alejandro-laptop kernel: [18993.277446] sd 7:0:0:0: [sdb] Mode Sense: 21 00 00 00
Aug  5 18:43:44 alejandro-laptop kernel: [18993.277519] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Aug  5 18:43:44 alejandro-laptop kernel: [18993.279209] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Aug  5 18:43:44 alejandro-laptop kernel: [18993.280805] sd 7:0:0:0: [sdb] Write Protect is off
Aug  5 18:43:44 alejandro-laptop kernel: [18993.280809] sd 7:0:0:0: [sdb] Mode Sense: 21 00 00 00
Aug  5 18:43:44 alejandro-laptop kernel: [18993.280812] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Aug  5 18:43:44 alejandro-laptop kernel: [18993.280818]  sdb: sdb1
Aug  5 18:43:44 alejandro-laptop kernel: [18993.324361] sd 7:0:0:0: [sdb] Attached SCSI disk
Aug  5 18:43:44 alejandro-laptop kernel: [18993.324433] sd 7:0:0:0: Attached scsi generic sg2 type 0
Aug  5 18:43:45 alejandro-laptop ntfs-3g[11684]: Version 2009.2.1 external FUSE 27 
Aug  5 18:43:45 alejandro-laptop ntfs-3g[11684]: Mounted /dev/sdb1 (Read-Write, label "My Passport", NTFS 3.1) 
Aug  5 18:43:45 alejandro-laptop ntfs-3g[11684]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=es_ES.UTF-8 
Aug  5 18:43:45 alejandro-laptop ntfs-3g[11684]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096 
Aug  5 18:43:45 alejandro-laptop hald: mounted /dev/sdb1 on behalf of uid 1000

```Parecería que está todo en orden, al menos no aparece nada de "panic".

Estoy tratando de entender cómo funciona testdisk, apenas lo logre, posteo la información.

Saludos y gracias,
Alejandro.

---

