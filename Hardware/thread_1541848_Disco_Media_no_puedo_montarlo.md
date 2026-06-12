---
title: "Disco Media no puedo montarlo"
date: 2010-07-29
forum: Hardware
---

### Post by akiestudio on 2010-07-29
Hola buenas , tengo un disco que pone Media , y cuando doy boton derecho montar, me pide la clave , la introduzco pero no pasa nada ,como podria montarlo ,
Esto es lo que sale con
sudo fdisk -l

/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       38913   158971207+   5  Extended
/dev/sda5           19123       20095     7815591   83  Linux
/dev/sda6           20096       20338     1951866   82  Linux swap / Solaris
/dev/sda7           20339       36751   131837391   83  Linux
/dev/sda8           36752       38913    17366233+   b  W95 FAT32

sudo /etc/fstab da.
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=faf1c49a-fb6c-45af-b5bc-0ca3c0213235 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=8cce0e01-b237-499d-bc1c-fae07763abe6 /home           ext3    relatime        0       2
# /windows was on /dev/sda8 during installation
UUID=5DDD-F971  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=116d9175-2837-432b-b593-7a15c273b2e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

pero claro no quise tocar porque me puedo cargar la particion de algun disco y no quiero...alguna ayuda, un saludo, 
Me gustaria poder aceder a C:/ de windos , porque puedo accepder a D:/ de windows desde   /windows...
Un saludo

---

### Post by guillermolisi on 2010-07-29
Por casualidad cambiaste la conexion de ese disco a la motherboard a una que no es la originalmente usada ?

Para mi el tema esta en que se modificaron los UUID y por eso no se montan automaticamente las particiones que estan en /etc/fstab.

---

### Post by akiestudio on 2010-07-30
Uso un portatil , asi que no he cambiado ninguna conexion....

Como podria montarlo un saludo

---

### Post by euzkoarima on 2010-07-31
Creo que falta en el fstab una entrada para /dev/sda1 que supongo es el disco C (al cual no puede acceder).
No estoy canchero en como agregar esa línea al fstab, ahí pido que otro que sepa más del tema opine.

Saludos,
Eduardo

---

### Post by biale on 2010-07-31
```
y cuando doy boton derecho montar, me pide la clave , la introduzco pero no pasa nada 
```

O haciendo doble click. ¿Alguna vez funciono de esa manera? me parece que el problema pasa por otro lado.

Con gparted fijate si aparece un signo de admiración para sda1. Si aparece no lo va montar.

gparted (gksu gparted) se puede instalar o correr desde el live cd.

Un saludo a todos.

---

### Post by akiestudio on 2010-07-31
Si aparece el triangulo  de la interrogacion , No hay manera de montarlo entonces?

---

### Post by biale on 2010-08-01
Solo si (usando gparted) aparece , el triangulo de alerta indica que hay un problema dentro de la misma partición! Es una herramienta de diagnóstico muy-muy importante.

---

### Post by akiestudio on 2010-08-01
Si que aparece en el Gparted, sabrias decirme como monto la particion , nunca he usado Gparted y tampoco soy un gran usuario de Ubuntu , y no quiero j***r la particion para no perder los datos , un saludo

---

### Post by biale on 2010-08-02
La reparación queda a cargo del utilitario de Windows. Arrancando WXP y  desde consola de DOS (WXP) "chkdsk C: /F" (sin las comillas). 

Alternativamente puede hacerse lo mismo desde el administrador de discos.

Y luego hay que reiniciar WXP para que lleve a cabo la comprobación como tarea programada.

El punto es "porque" aparecieron problemas en la partición. Como las causas pueden ser varias, merece un seguimiento.

---

### Post by akiestudio on 2010-08-06
Ya probe eso y siguen apareciendo el triangulo amarillo y  si poder montarse,alguna otra sugerencia 
Gracias

---

### Post by akiestudio on 2010-08-06
Lo consegui montar con:

sudo mount -t ntfs-3g /dev/sda1 /media/windows

pero aparece un simbolo de un al lado le doy y aparece:

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Pero cuando reinicio aparece desmontado

Alguna ayuda

---

### Post by biale on 2010-08-06
El mensaje dice que hubo un intento de acceso que no se completo. 

Hay que descartar un mal cierre de Windows que deje a la partición como "no montable". Visor de eventos?

Y luego descartar algun problema en Ubuntu. Eso puede hacerse con algún arranque Linux live de lo que sea.

Curiosidad: en mi instalacion de Lucid no pide clave para montar ninguna partición. Si las pedía karmic.

---

