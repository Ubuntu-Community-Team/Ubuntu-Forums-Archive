---
title: "[SOLUCIONADO] No puedo guardar archivos en pendrive"
date: 2009-06-10
forum: Hardware
---

### Post by vtssrm on 2009-06-10
Compre una pendrive de 4GB (venía con una partición FAT32), luego formatie esta unidad con una partición de tipo EXT4 con el programa GParted, desmonto la unidad, la vuelvo a enchufar, hasta ahí ningún drama, pero a la hora de querer copiar un archivo dentro me dice que "no tengo los permisos"...

¿Qué debo hacer para poder comenzar a guardar mis archivos en EXT4 o tendré que formatear la unidad en FAT32?

También me fije que al formatear en EXT4, en el directorio raíz de la pendrive se creo una carpeta llamada "lost-found" que además no puedo eliminar... ¿Por qué?

---

### Post by Carlos C on 2009-06-10
Trata de copiar usando sudo. Si te resulta es porque tienes que modificar los permisos de la unidad para que te permita escribir sobre la partición que creaste en tu pendrive. Puedes ver los permisos de la partición abriendo Nautilus y haciendo click derecho sobre tu unidad de pendrive y escogiendo, en el menú contextual, la opción propiedades-->permisos.

La carpeta lost+found no debes borrarla, ya que en caso de que tengas un problema con tu unidad el sistema realiza un chequeo de la misma y deja en esa carpeta cualquier dato corrupto, probablemente dañado, que haya podido rescatar. Si te fijas en el resto de tus particiones verás que esta carpeta está presente en todas ellas.

---

### Post by vtssrm on 2009-06-10
Ya, entre con consola así

$ sudo nautilus

y entre a las propiedades de la pendrive y me fui a la pestaña de permisos. Cambie el propietario de root a "mi usuario", también el de Grupo y Otros.

Ahora ya puedo copiar y crear archivos como queria. Gracias!!!

--Solucionado--

---

### Post by gmunioz on 2009-06-10
Hola vts...:

Como hace años que no uso el operativo de Microsoft, mis pendrives

estan en sistema de archivos nativos de gnulinux.

la solución que has aplicado, te servirá únicamente para ese

ordenador, más si lo usas en otro el problema reaparecerá.

La solución definitiva que encontré para poder utilizarlos entre

los distintos ordenadores (trabajo - casa - amigos - etc. etc.)

Fue crear un directorio, en mi caso para ser original /dir y darle

permisos de lectura escritura por todos ejecutando en consola con

el dispositivo montado:

```
sudo chmod -Rf 777 /media/Kingston/dir
```

A partir de esto, puedo utilizar mis pendrives en todos los 

ordenadores con gnulinux sin problemas de permisos, copiando y

borrando dentro del directorio /dir.

---

### Post by CdK1 on 2009-06-10
Yo que tú no lo hubiese "formateado" con EXT4, lo hubiere dejado por defecto, y como te ciden creo un directorio tipo /media/pendrive y usaría 3g-ntfs para montarlo automaticamente con permisos desde fstab y me ahorro dramas, ya que dudo que un PC con Win te deje leerlo...

---

### Post by radixs on 2009-06-12
> **CdK1 said:**
> Yo que tú no lo hubiese "formateado" con EXT4, lo hubiere dejado por defecto, y como te ciden creo un directorio tipo /media/pendrive y usaría 3g-ntfs para montarlo automaticamente con permisos desde fstab y me ahorro dramas, ya que dudo que un PC con Win te deje leerlo...

Estoy de acuerdo con Cdk1 ya que cuando vayas a algun lugar y tengan win... ups! no lee el pendrive.

---

### Post by vtssrm on 2009-06-19
> **CdK1 said:**
> Yo que tú no lo hubiese "formateado" con EXT4, lo hubiere dejado por defecto, y como te ciden creo un directorio tipo /media/pendrive y usaría 3g-ntfs para montarlo automaticamente con permisos desde fstab y me ahorro dramas, ya que dudo que un PC con Win te deje leerlo...

> **radixs said:**
> Estoy de acuerdo con Cdk1 ya que cuando vayas a algun lugar y tengan win... ups! no lee el pendrive.

Gracias por las advertencias pero filo con Windows, hay que dejar de preocuparse por ser compatible con ellos, ahora que ellos se preocupen de nosotros.

---

### Post by Psycopatologic on 2009-06-19
por experiencia y por vida academica prefiero mil veces usar un pendrive formateado en NTFS o FAT32 y montarlo con ntfs-3g, que es lo que hago ahora. 

La razon? el 90% de los pc que uso tienen windows, los de las salas de clases cuando tengo que exponer, los de los lab de computacion, el notebook de mi viejo, el pc de la polola, etc. Decir "preocupemonos de nosotros" es algo excluyente, te automarginas ya que todos sabemos que sistema manda en estos momentos. Ademas, es mucho menos aparatoso que formatearlo como ext4 ya que ntfs-3g te deja montar, escribir y leer por defecto sin permisos especiales, en cambio para ext tienes que asignar permisos.

Si aun quieres seguir con lo de ext te recomiendo hagas lo que dice Gmunios

sudo chmod -Rf 777 /media/Kingston/dir
y donde dice Kingston reemplazas por el nombre de tu unidad flash.

saludos

---

### Post by vtssrm on 2009-06-20
> **Psycopatologic said:**
> por experiencia y por vida academica prefiero mil veces usar un pendrive formateado en NTFS o FAT32 y montarlo con ntfs-3g, que es lo que hago ahora. 

La razon? el 90% de los pc que uso tienen windows, los de las salas de clases cuando tengo que exponer, los de los lab de computacion, el notebook de mi viejo, el pc de la polola, etc. Decir "preocupemonos de nosotros" es algo excluyente, te automarginas ya que todos sabemos que sistema manda en estos momentos. Ademas, es mucho menos aparatoso que formatearlo como ext4 ya que ntfs-3g te deja montar, escribir y leer por defecto sin permisos especiales, en cambio para ext tienes que asignar permisos.

Si aun quieres seguir con lo de ext te recomiendo hagas lo que dice Gmunios

sudo chmod -Rf 777 /media/Kingston/dir
y donde dice Kingston reemplazas por el nombre de tu unidad flash.

saludos

“Nadie puede servir a dos señores; porque aborrecerá a uno y amará al otro; o bien se entregará a uno y despreciará al otro. No podéis servir a Dios y al Dinero”

te lo traduzco...

“Nadie puede servir a dos sistemas operativos; porque aborrecerá a uno y amará al otro; o bien se entregará a uno y despreciará al otro. No podéis servir a UBUNTU y a WINDOWS”

Espero tu respuesta...

---

### Post by moreback on 2009-06-20
No puedes amar ni servir a algo que no existe.

Saludos.

PD: por favor, no mezclemos religiones con sistemas operativos.

---

### Post by Carlos C on 2009-06-22
Ya. Creo que la consulta fue respondida y no creo que el tema de para mucho más (me refiero a la consulta original). Por favor evitemos desviar la conversación hacia otra cosa. Muchas gracias a todos los que amablemente respondieron. Voy a editar el título del thread para darlo por solucionado.
Saludos.

---

### Post by Soushiro on 2009-07-27
> **vtssrm said:**
> “Nadie puede servir a dos señores; porque aborrecerá a uno y amará al otro; o bien se entregará a uno y despreciará al otro. No podéis servir a Dios y al Dinero”

te lo traduzco...

“Nadie puede servir a dos sistemas operativos; porque aborrecerá a uno y amará al otro; o bien se entregará a uno y despreciará al otro. No podéis servir a UBUNTU y a WINDOWS”

Espero tu respuesta...

La idea de la informatica es aprovechar los recursos que se nos ponen por delante, y disfrutarlos. no creo que sea buena idea Inmolarse en nombre de un S.O. yo por mi parte tengo instalado Ubuntu y Xp prof. en el mismo computador y utilizo ambos, segun sea el caso que lo necesito.

---

### Post by solipanta on 2012-09-24
tengo un problema similar, el sistema dice que esta conectado pero no lo monta, todo comenzo luego de darle formato (ext4)cuando en el creador de discos de arranque le di a la opcion borrar

me da este error

org.freedesktop.UDisks.Error.Failed: Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=0, size=8351866880, type=0x0c
Entering MS-DOS parser (offset=0, size=8351866880)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed

---

