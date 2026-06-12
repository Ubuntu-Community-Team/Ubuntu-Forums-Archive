---
title: "20 GB perdidos en partición virtual"
date: 2009-03-20
forum: Hardware
---

### Post by Criminel on 2009-03-20
Hola,
Siguiendo consejos leídos en foros - y para recuperar 20GB de una partición que tenía en XP sobre un disco total de 80GB - cree una partición sda3. Soy novato en esto y el tema es que parece estar montada en /media (así aparece cuando veo el uso del disco en el monitor del sistema) pero no sé cómo acceder a esos 20GB para que aparezcan como soporte en donde guardar archivos. Es decir, tengo 20GB que no puedo usar ni unir a Ubuntu porque no sé dónde ni cómo se "activan"

Agradeceré cualquier ayuda.

---

### Post by fmsismo on 2009-03-21
Escribi el comando mount y verificamos que este montada?

[INDENT]mount[/INDENT]

y te devuelve algo como 

[INDENT]usuario@terminus:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,noatime)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
[/INDENT]

Con el resultado del comando vemos como seguimos.

---

### Post by Criminel on 2009-03-22
drutus@drutus-desktop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda3 on /media type ext3 (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/drutus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=drutus)


Ahí fue.

---

### Post by fmsismo on 2009-03-22
> **Criminel said:**
> drutus@drutus-desktop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda3 on /media type ext3 (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/drutus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=drutus)


Ahí fue.

Según lo que te devuelve esto el /dev/sda3 es un ext3.

Hace un 

sudo fdisk -l /dev/sda

Esto va a listar todas las particiones que tiene tu disco.

En un equipo mio devuelve:

sudo fdisk -l /dev/sda
[sudo] password for usuario:

Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00050507

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  83  Linux
/dev/sda2              63        5221    41439667+  8e  Linux LVM

Que te devuelve a vos?


Saludos

---

### Post by Criminel on 2009-03-23
Disco /dev/sda: 80.0 GB, 80032038912 bytes
255 cabezas, 63 sectores/pista, 9730 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x70994fbd

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          47      377496   83  Linux
/dev/sda2            2862        9730    55175242+   5  Extendida
/dev/sda3              48        2861    22603455   83  Linux
/dev/sda5            2862        9444    52877916   83  Linux
/dev/sda6            9445        9730     2297263+  82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

Eso.

---

### Post by fmsismo on 2009-03-23
Ok, por lo que vemos ahora, no tenes ninguna partición ntfs o fat.  Si queres usarla para área de intercambio con windows, tenes que usar alguno de estos dos sistemas de archivos (podes poner un driver para que windows vea los ext3 como ext2, pero no es lo más sano del mundo, sobre todo si el windows se cuelga, lo que no es extraño).


Si queres usar la partición /dev/sda3, ya la tenes montada en el /media.  Si queres montarla en otro punto de montaje, como un /home/mengano/donwloads o algo por el estilo te puedo ayudar.

Si queres instalar el xp en esa partición es un bardo aparte, pero seguro lo podemos sacar adelante.

Saludos

---

### Post by Criminel on 2009-03-23
Justamente, no quiero windows ni nada de eso. Lo que busco es montarla en otro lado que no sea /media y usarla para guardar archivos (como bien decís en tu opción número dos).
El tema es que así como está ahora (montada en /media) ni la veo ni puedo acceder a ella para guardar archivos allí.

Gracias.

---

### Post by Hei Ku on 2009-03-23
Anda al administrador de discos, y desde ahi podes cambiarle los permisos a la particion. Ahora debe estar con permisos solo para root.

---

### Post by Criminel on 2009-03-24
Al hacerlo - y darle "enable" desde el admin. de discos  me aparece una carpeta llamada DATOS (el nombre que le puse a esa part.) dentro de media, pero el árbol de carpetas aparece como sigue:

media
cdrom0
DATOS
los and found

y dentro de DATOS, otra vez tengo

DATOS (como una subcarpeta).

El tema es que no me permite copiar y pegar datos ahí.

¿Alguna idea?

---

### Post by fmsismo on 2009-03-24
Tenes que darle permisos para que tu usuairo pueda escribir o todos los usuarios.

Si la carpeta que creaste es /media/datos

Y queres que solo tu usuairo tenga permisos para escribir, donde usuario es el nombre de tu usuario.

sudo chown usuario:usuario /media/datos

Si queres que todo el mundo pueda escribir.

sudo chmod 777 /media/datos

Saludos

---

### Post by Criminel on 2009-03-24
Acabo de hacer algo muy mal.
Intebnté lo que dijiste y no funcaba.
Cambié el punto de montaje de media a home y ahora no tengo acceso a nada.

Help please.

---

### Post by Criminel on 2009-03-24
Algo hice mal. 
Luego de que no resultaran los comandos que me diste (la respuesta es que no existia esa part) cambié el punto de montaje de /media a /home...
Ahora no tengo acceso a nada.

¿Se puede deshacer o perdí todo?

---

### Post by fmsismo on 2009-03-24
Ok, don't panic.

Los comandos que te pase eran para cambiar el owner y los permisos.

Cual de los dos ejecutaste?

---

### Post by Criminel on 2009-03-25
Solucionado. Aunque no de la mejor manera.

Terminé aprovechando el moco que me mandé y formatée el disco entero (tenía backup de lo importante), con lo cual ya recuperé los 20GB.

En fin, aprenderé la próxima vez.

Gracias por la asistencia.

---

