---
title: "me dejo de bootear mi ubuntu ='("
date: 2008-08-19
forum: Hardware
---

### Post by mansaneitor on 2008-08-19
hola como dice el titulo del thread, venía usando ubuntu HH 8.04... hasta q hoy, al intentar bootear me salta el siguiente error

```
Check root= bootarg cat /proc/cmdline
      or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/05defadb-2dd2-48e7-ba76-1b89a7ac71ef does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
```

alguna idea y/o solución?, venía andando todo perfecto ='(

---

### Post by pol666 on 2008-08-19
modificaste el fstab el grub o moviste alguna particion?

---

### Post by mansaneitor on 2008-08-20
no modifiqué absolutamente nada =/

googleando leí x ahí que tengo q montar de nuevo una partición "x", pero ni idea de como hacerlo

---

### Post by Lokkete on 2008-08-20
no es la solución más técnica pero probaste booteando con el ubuntu recovery? o no te llega  esa opcion? 

sino carga un kernel mas viejo y luego actualizalo, aveces es mas practico volver para atras un poco que solucionar una solución específica

---

### Post by mansaneitor on 2008-08-20
pero no entiendo.. si yo no modifiqué absolutamente nada =/ q onda

encima soy un newbie en lo q tiene q ver con ubuntu ajJA

---

### Post by Lokkete on 2008-08-20
el problema ya lo tenes yo que vos busco alguna solucino...puede haber sido algun update o algun sector del rigido dañado o memoria dañada que te carga mal el software....:P proba el recovery

---

### Post by mansaneitor on 2008-08-23
con la ayuda de otro miembro del foro traté de ver si la partición tenía algún problema, ejecutando desde la consola "sudo gparted" (con un live cd), y miren lo que me salta :O 

[[IMG]http://img353.imageshack.us/img353/3493/pantallazohs6.th.png[/IMG]](http://img353.imageshack.us/my.php?image=pantallazohs6.png)

no le puedo hacer absolutamente nada desde gparted a la partición... salvo formatearla =/

alguna idea? thx =)

---

### Post by pol666 on 2008-08-23
se **** el sistema de archivos lamentablemente se tendra que formatear,. Fiajte si podes copiar los datos a otro disco para no perder todo

---

### Post by Hei Ku on 2008-08-23
Fijate si con dd podes hacer una copia a otro disco, y proba despues de correrle un fsck, a ver si podes recuperarla.

---

### Post by mansaneitor on 2008-09-09
> **pol666 said:**
> se **** el sistema de archivos lamentablemente se tendra que formatear,. Fiajte si podes copiar los datos a otro disco para no perder todo

despues de un par de semanas, formatee mi hd...
instale HH 8.04, de 0 y pasa exactamente lo mismo q antes, tira el mismo error y no bootea :S
ni idea que puede ser, alguna idea? =/

---

### Post by Afkael on 2008-09-09
mmm.. quizá tengas que comprobar la integridad de ese disco, no creo que sea un problema del SO.
Yo arrancaria de la liveCD, aunque no conozco los programas que trae.. en este thear de otro foro se nombran algunas herramientas... espero te sirvan

[http://blogdrake.net/node/11506](http://blogdrake.net/node/11506)

Saludos

---

### Post by mansaneitor on 2008-09-09
oka, cuando llego del laburo pruebo =)

pero igualmente dudo mucho q sea el hd (le pase 1984928392 scans de todo lo q se te ocurra y nunca tiro un error), para mi es un problema con las particiones montadas... 

que comandos puedo usar para ver si estan bien montadas las particiones (no se como se montan) jaJAJA

off: googleando ya vi muchísimas veces este error, pero nunca la solución =/

grax =D

---

### Post by faktorqm on 2008-09-09
El tema del UUID tengo entendido que es un hash interno, lo que podes probar es poner directamente en tu /etc/fstab el dispositivo para que te lo monte y asi recuperar la cosa.

En mi fstab tengo esto:

```

faktorqm@the-edge:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5430a0a1-0ca4-4304-b2b5-d682a2ff0f43 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=77d32be4-949e-4eb7-9ee6-ace2419cf5f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
faktorqm@the-edge:~$ 

```

y lo podrias cambiar por

```
/dev/sda1     /               ext3    relatime,errors=remount-ro 0  
```

en mi caso claro, en el tuyo te tenes que fijar que dispositivo es. El archivo lo editas con "sudo gedit /etc/fstab" (sin comillas) y reiniciar. Con un live CD por supuesto. Lo pones lo editas y reinicias. Salu2!

---

### Post by mansaneitor on 2008-09-10
faktorqm probé hacer lo que me dijiste, perooooooo al ejecutar "sudo gedit /etc/fstab"

me aparece solamente lo siguiente (en el archivo)

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

como lo tendría q editar?

off:

sda1 es mi partición ext3  (en gparted me sale con un signo de "!" y me dice q no esta montada)
sda2 extended
 y   sda5 swap

---

### Post by faktorqm on 2008-09-11
uh! y eso? jamas lo habia visto antes... 

hace una cosa, vacapeá ese archivo (uno nunk sabe...) con 

```
sudo cp /etc/fstab /etc/fstab_viejo
```

y tira un "sudo fdisk -l" (sin comillas) asi listamos todas las particiones de tu disco rigido e intentamos armar un fstab nuevo. No conozco si hay una herramienta para re generarlo automaticamente...

Salu2!

---

### Post by mansaneitor on 2008-09-11
cuando le tiro ese comando q me dijiste para listear las unidades de disco, no me tira nada... como q no puede acceder a las particiones =/

ningún comando relacionado con las unidades de disco funciona =(

ya no se q hacer................

---

### Post by faktorqm on 2008-09-11
esteemmm la verdad que yo tampoco, como puede ser que no te liste las particiones de los discos... estas desde un live cd? es sata el disco? capaz no te reconoce el disco o tiene problemas con el driver sata y entonces no "ves" el disco. salu2!

---

### Post by fmsismo on 2008-09-11
Desde el live cd hace lo siguiente:

sudo ls -lh /dev/sd*

Esto te va a listar los dispositivos SCSI que tengas.  Te devuelve algo como esto:

[INDENT]sismo@sismo-desktop:~$ sudo ls -lh /dev/sd*
[I]brw-rw---- 1 root disk 8,  0 2008-09-11 06:17 /dev/sda
brw-rw---- 1 root disk 8,  1 2008-09-11 06:17 /dev/sda1
brw-rw---- 1 root disk 8,  2 2008-09-11 06:17 /dev/sda2
brw-rw---- 1 root disk 8,  3 2008-09-11 06:17 /dev/sda3
brw-rw---- 1 root disk 8,  4 2008-09-11 09:17 /dev/sda4
brw-rw---- 1 root disk 8,  5 2008-09-11 06:17 /dev/sda5
brw-rw---- 1 root disk 8, 16 2008-09-11 09:17 /dev/sdb
brw-rw---- 1 root disk 8, 17 2008-09-11 09:17 /dev/sdb1
sismo@sismo-desktop:~$ [/I]
[/INDENT]

Luego si ves algún disco (en mi equipo lista dos discos, un sda y un sdb) podes hacer un fdisk -l /dev/sd***X***

Que en mi caso (lo hice sobre los dos discos).

[INDENT]sismo@sismo-desktop:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3610c57f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3837    30820671    7  HPFS/NTFS
/dev/sda2            3838        9100    42275047+   f  W95 Ext'd (LBA)
/dev/sda3           19204       19452     2000092+  82  Linux swap / Solaris
/dev/sda4            9101       19203    81152347+  83  Linux
/dev/sda5            3838        9100    42275016    7  HPFS/NTFS

Partition table entries are not in disk order
sismo@sismo-desktop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7296    58605088+  83  Linux
sismo@sismo-desktop:~$ 
[/INDENT]

Copianos acá en el foro que te devuelven estos comandos, y vemos de rearmar tu fstab de vuelta.

En caso de que no te detecte ningún disco, fijate de bajarte y quemar la iso nueva del intrepid 

[http://cdimage.ubuntu.com/releases/8.10/alpha-5/intrepid-desktop-i386.iso](http://cdimage.ubuntu.com/releases/8.10/alpha-5/intrepid-desktop-i386.iso)

Si es un tema de drivers pude que la versión nueva te lo resuelva.

Otra cosa que podes ver es si el problema no vino con un kernel nuevo.  Cuando inicia, fijate si podes hacer que bootee desde otro más viejo.

Suerte

---

### Post by mansaneitor on 2008-09-11
> **faktorqm said:**
> esteemmm la verdad que yo tampoco, como puede ser que no te liste las particiones de los discos... estas desde un live cd? es sata el disco? capaz no te reconoce el disco o tiene problemas con el driver sata y entonces no "ves" el disco. salu2!

es un disco ide de 80gb marca western digital

----

off: aca hice lo q me dijiste fmsismo a ver si te sirve

```
ubuntu@ubuntu:~$ sudo ls -lh /dev/sd*
brw-rw---- 1 root disk 8, 0 2008-09-11 15:17 /dev/sda
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x60166016

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extendida
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

off: al principio me habia pasado por una actualización... pero despues formatee e instale todo desde un cd de ubuntu (el q me llego de shipit)

---

### Post by fmsismo on 2008-09-11
Ok, el disco ubuntu lo ve.

Hora me gustaría que veas que tenes en el fstab.  El tema es que si esto lo estas haciendo desde el livecd, el fstab que tenes en el /etc/fstab no se sirve.

Si este es tu caso tenes que tenerlo montado en /media /mnt o sino montalo.

sudo mkdir -p /media/sda1
sudo mount /dev/sda1 /media/sda1
cat /media/sda1/etc/fstab  (lo que te devuelva esta línea pegalo).

Avisame si te encontras con algún inconveniente.  Y vemos de seguir amacando el problema.

Saludos

---

### Post by mansaneitor on 2008-09-12
> **fmsismo said:**
> Ok, el disco ubuntu lo ve.

Hora me gustaría que veas que tenes en el fstab.  El tema es que si esto lo estas haciendo desde el livecd, el fstab que tenes en el /etc/fstab no se sirve.

Si este es tu caso tenes que tenerlo montado en /media /mnt o sino montalo.

sudo mkdir -p /media/sda1
sudo mount /dev/sda1 /media/sda1
cat /media/sda1/etc/fstab  (lo que te devuelva esta línea pegalo).

Avisame si te encontras con algún inconveniente.  Y vemos de seguir amacando el problema.

Saludos

a la carpeta la pude crear con mkdir, pero cuando le tiro mount... me dice que la partición no existe...

off: mepa q voy a intentar formatear de nuevo, en q es mejor formatear ntfs? fat32? 

thx4all ;)

---

### Post by fmsismo on 2008-09-12
Si vas a instalar ubuntu, borra todas las particiones y larga con la instalación de 0, como si fuera un disco nuevo.  Va a usar ext3 que es lo estandar, si vas usar XP te conviene ntfs, sobre todo si tenes un disco grande.

Con esto que me decis vi tu problema.  El disco esta particionado, pero es sistema no ve las particiones.

Esto lo estas haciendo desde el livecd no?


Saludos

---

### Post by mansaneitor on 2008-09-12
no, no hay forma... formatee de nuevo y sigue el mismo error :S osea no se más q hacer, ni a quien consultarle =/

off: no existe un canal de irc copado, en donde pueda consultar?

thx =D

off2: acabo de leer en este thread [http://ubuntuforums.org/showthread.php?t=649135](http://ubuntuforums.org/showthread.php?t=649135) que un loco lo soluciono metiendo mano en el MBR del hd, alguien sabe alguna herramienta (para xp o ubuntu) q funke bien para eso?

EDIT: ya lo solucione... pase el mbr-fix booteando con un minipe, tire el cable ide porque estaba viejito, puse uno nuevo, prendi la pc y booteo 10puntos ;)

thx a los q me ayudaron =D

---

