---
title: "El Lector de DVD lee lo que quiere"
date: 2008-07-29
forum: Hardware
---

### Post by Sawady on 2008-07-29
Saludos...
Bueno, cansadisimo de no encontrar respuesta...
Puedo visualizar los archivos de ahi a copiarlos al disco o si son peliculas visualizarlos hay un paso enorme... busque y busque y parece un problema con el DMA, un bug del kernel con drivers ATA y problemas con IDE, y ya ni se que mas decian por ahi...

Miren lo que me tira al intentar hacer esto:

> 
sempron@sempron-desktop:~$ sudo hdparm /dev/dvd

/dev/dvd:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for deviceç

hermoso no?

Por ahi lei (en ingles obvio) que habia que compilar un nuevo kernel poniendo como blacklisted cierto modulo ata... pero la verdad no entendi nada y tampoco me quiero meter ahora a compilar un kernel...

La lectora anda barbara en XP, y no tiene nada q ver si el DVD es -r o +r... pasa con cualquier marca...

Tengo conectadas por IDE esta grabadora de DVD y una grabadora de CD... la de cd anda barbaro :@

Alguna idea de como solucionar esto?

Por cierto:
2.6.24-20-generic

PD: debe ser por actualizar por actualizar el Kernel... ademas de este problema no se imaginan lo que me pelee con virtualbox (igual ta solucionado, ahora puedo dar catedra en el tema xD)

Desde ya gracias...

---

### Post by Hei Ku on 2008-07-30
Te acordas que modulo habia que poner como blacklisted? Porque hay una forma de agregarlo sin necesidad de compilar. Al menos como para hacer la prueba.

---

### Post by Sawady on 2008-07-30
esta es la pag donde termine luego de leer muchos post diferentes:
[https://bugs.launchpad.net/ubuntu/+bug/175022](https://bugs.launchpad.net/ubuntu/+bug/175022)

Lo que dice mysticism en ese post es:
> I have the same problem on Ubuntu Hardy Heron with a Samsung TS-H552B (TSSTcorpCD/DVDW) and 2.6.24-5 Kernel running on an MSI RS480M2/RX480M2 motherboard. If I tried to play a DVD its playback was slow and jerky. Looking on the Ubuntu forums I found that the problem might be that DMA wasn't enabled so I ran:
 $ sudo hdparm -d1 /dev/scd0
     setting using_dma to 1 (on)
     HDIO_SET_DMA failed: Inappropriate ioctl for device

Then following a tip from a forum post I ran
$ dmesg
   ...
   [ 35.286790] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H552B, GA04, max UDMA/33
   [ 35.286804] ata2.00: simplex DMA is claimed by other device, disabling DMA
   ...

Then searched Ubuntu forums for "simplex DMA" and found these posts [http://ubuntuforums.org/showthread.php?t=435706](http://ubuntuforums.org/showthread.php?t=435706) and [http://ubuntuforums.org/showthread.php?t=678153](http://ubuntuforums.org/showthread.php?t=678153)
Folowing the advice in the first post I ran:
$ lsmod | grep -i ^libata”
   libata 176304 4 pata_acpi,sata_sil,ata_generic,pata_atiixp

Then following the advice in the second post in reply #9 I blacklisted the ata_generic module.
WARNING BLACKLISTING THE WRONG MODULE CAN RESULT IN A NON BOOTABLE MACHINE
I did this by opening the file /etc/initramfs-tools/modules and adding these lines at the bottom:
  pata_atiixp
  blacklist ata_generic

Then I recreated the initramfs with
$ sudo update-initramfs -u

Then after rebooting the CDROM drive now has DMA enabled and the DVD's playback smoothly.

From this it appears that there is a bug in the ata_generic module that prevents DMA from being enabled on some CDROM Drives on some computers.


Desde ya gracias...

---

### Post by Hei Ku on 2008-07-30
De acuerdo tendrías que fijarte primero si te esta cargando ese modulo, y en ese caso, agregarlo a la blacklist, que no implica recompilar, no te preocupes.

Como diria Jack, vamos por partes:

Fijase si te está cargando el módulo:
```

lsmod | grep -i ^libata&#8221;

```

Si te aparece listado el ata_generic, entonces vas a agregarlo a la blacklist.

Apretas alt+F2 y ponés
```

gksudo gedit /etc//etc/modprobe.d/blacklist

```

Y al final del archivo le agregas una linea que diga:

```

blacklist ata_generic

```

Guardas el archivo, cerras y reinicias.

Tené un LiveCD a mano, porque quizás después de esto no arranca más. :lolflag:

---

### Post by Sawady on 2008-07-30
hice todo... probe poniendo como blacklist ata_generic y tamb probe poniendo libata y nada... arranca todo bien, pero parece que hasta siguen cargados esos modulos...

ata_generic             8324  0
libata                159344  4 pata_acpi,sata_nv,ata_generic,pata_amd

tambien me fije si aparecian cargados en /etc/modules y no estaban...

sigo leyendo pero no hay caso, en otras versiones de ubuntu funcionaba, ahora en hardy resurgio ese problema y justamente segun leo porque hay un conflicto con ese ata_generic que no deja activar el DMA...

alguna otra idea?

Hei Ku muchas gracias por preocuparte...

---

### Post by Hei Ku on 2008-07-31
Proba lo siguiente:

Alt+F2 y pones:
```

gksudo gedit /etc/initramfs-tools/modules

```

y al final del archivo agregas:
```

pata_atiixp
blacklist ata_generic

```

Grabá, cerrá y reiniciá. Misma advertencia que el post anterior. Suerte!

---

### Post by Sawady on 2008-08-02
sigue cargando los modulos...

uff... mas que por las peliculas, tengo mucha informacion en DVDs y que me lea dvds es una funcion primaria xD

Voy a probar con el livecd para ver si desde ahi puedo leer dvds... si es eso volvere a una version anterior del kernel...

Si tienen alguna otra idea por favor posteen...

Saludos y gracias...

edit: nada q ver el kernel xD... no se q pasa... tal vez ubuntu monte mal el dvd, pero ya intente desmontando y montando de varias maneras y sigue pasando...

edit2: miren lo que dice aca
> sempron@sempron-desktop:~$ dmesg | tail
[ 1308.557467] Buffer I/O error on device sr0, logical block 2193584
[ 1308.557469] Buffer I/O error on device sr0, logical block 2193585
[ 1308.557471] Buffer I/O error on device sr0, logical block 2193586
[ 1308.557473] Buffer I/O error on device sr0, logical block 2193587
[ 1308.557476] Buffer I/O error on device sr0, logical block 2193588

otra cosa, es como si leyera las primeras pistas y las que restan no, porque siempre hay algunos videos que se llegan a reproducir al principio pero lo demas no, se traba y se sale el reproductor, o dice "no se pudo leer el recurso" o los copias al rigido y dicen "error de lectura/escritura"...

tambien lo que figura en el fstab por si alguno se percata de algo:

> /dev/scd1	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/scd0	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0

---

### Post by Hei Ku on 2008-08-03
Corriste este comando al final, despues de hacer el cambio? Me habia olvidado de ponerlo.

sudo update-initramfs -u

---

### Post by Sawady on 2008-08-03
sep... segui el tutorial tuyo y el del foro en ingles al pie de la letra... algunos usuarios de esos foros postearon que luego de hechos esos pasos, el dvd les volvio a funcionar aunque el modulo siguio cargado, pero no es mi caso...

probe con el livecd de ubuntu y pasa lo mismo. Instale puppy linux en mi pendrive y el dvd lo monta perfectamente y no hay problemas, asi que el bug debe provenir de ubuntu...

descargue tambien el paquete UDFtools pero igual no pasa nada...

---

### Post by Hei Ku on 2008-08-03
Fijate el fstab que usa el puppy linux y también la lista de modulos que carga, a ver si hay alguna diferencia. Capaz de ahi podemos sacar alguna conclusión.

---

### Post by Sawady on 2008-08-04
La diferencias son:

> Ubuntu:

fstab
/dev/scd0	/media/cdrom0	iso9660,udf user,noauto,exec,utf8 0 0

lsmod:
libata                159344  4 pata_acpi,sata_nv,ata_generic,pata_amd
scsi_mod              151436  5 sg,sd_mod,sr_mod,usb_storage,libata

hdparm /dev/scd0:
IO_support    =  0 (default) 
16-bit)
HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
HDIO_GET_DMA failed: Inappropriate ioctl for device
HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
readonly      =  0 (off)
readahead     = 256 (on)
HDIO_GETGEO failed: Inappropriate ioctl for device


> Puppy:

fstab: no figura nada ni del rigido ni del las lectoras, aunque las monta
porque en el mtab figura esto:
/dev/hda /mnt/hda iso9660 ro 0 0

lsmod:
ide_cd 39200 1
cdrom 36768 2 sr_mod,ide_cd

hdparm /dev/hda:
mulcount = 128 (on)
IO_support = 1 (default 32-bits)
using_dma = 1 (on)
unmaskirq = 1 (on)
readonly      =  0 (off)
readahead     = 256 (on)
HDIO_GETGEO failed: Inappropriate ioctl for device 

Conclusion, en puppy no esta ata_generic y ademas carga las lectoras como hda y hdb, mientras ubuntu las carga como scd0 y scd1...

Probe muchas configuraciones distintas, sacando UDF, poniendo hda en vez de scd, sacando algunas opciones como user,noauto,exec,utf8, pero no pasa nada... seguramente es ese modulo que carga el kernel y que reconoce mal al dispositivo...

voy a probar de hacer todos los pasos de vuelta...

edit:

no se si tiene que ver pero:

> sempron@sempron-desktop:~$ sudo update-initramfs -u
[sudo] password for sempron: 
update-initramfs: Generating /boot/initrd.img-2.6.24-19-386

y el kernel que estoy usando es 2.6.24-20-generic

---

### Post by Hei Ku on 2008-08-04
Fijate los paquetes de kernel que tenes? Tenes algo que pertenezca al 24-19, como los headers?

---

### Post by Sawady on 2008-08-04
si, lo selecciono al momento del grub pero no termina de cargar el SO y queda ahi... ctrl+alt+supr y reinicio...

ademas cargar un kernel anterior me va a traer conflictos con el kernel que usa virtual box :S

---

### Post by Hei Ku on 2008-08-04
no, justamente te preguntaba porque en Synaptic solo te deberian figurar como instalados los paquetes del 2.6.24-20, no los del 19. Por alguna razon está haciendo la actualizacion para el anterior.

---

### Post by Sawady on 2008-08-05
bueno... lo solucione por mi cuenta... ahora tambien doy catedra de drivers para canales ide (jajaja)...

cada post que leia tenia una solucion diferente, pero ninguna me funcionaba...

primero desinstale los headers y lo demas anterior al kernel actual para poder hacer "update-initramfs -u" y que justamente tenga efecto sobre este kernel... lo hizo bien, reinicio, pero no pasa nada...

sigo buscando en google, otro tema parecido a los que venia leyendo, solo que aqui llega a la conclusion de que esto sucede con chipsets marca VIA o AMD cuando se tienen dos lectoras en un mismo canal IDE... daban la solucion poniendo en blacklisted a los drivers pata_amd (o pata_via)...

Hago esto al igual que lo hice con ata_generic y pata_atiixp, pero no pasa nada...

Es ahi cuando ya me puse a leer todo sobre el funcionamiento del fstab y drivers que se cargan en el kernel... resulta que los drivers se encuentran en el directorio "/lib/modules/2.6.24-20-generic/kernel/drivers"... inspecciono cada sub-directorio hasta toparme con "ide"... ahi analizo bien que poner en el "/etc/initramfs-tools/modules", y por logica elijo y agrego: ide_generic, ide_cd e ide_generic.

Compilo, reinicio y ahora funciona todo a la perfección.

ahora carga el dvd en /dev/hda...

Muchas gracias Hei Ku por la paciencia y la buena onda...

Fue una real tortura, pero el resultado valio la pena... por fin disfruto de leer datos de dvd en mi ubuntu y ademas aprendi un poquito mas sobre GNU/linux...

Saludos...

---

### Post by Hei Ku on 2008-08-05
Una medallita por la paciencia y el esfuerzo. Ojala todos le pusieran tanta garra. :)

---

