---
title: "Sobre particiones y sistemas de archivos"
date: 2008-12-02
forum: Hardware
---

### Post by Thalskarth on 2008-12-02
Buenas, ultimamente he estado leyendo un poco sobre éste tema y en varios lugares comentan que es conveniente tener separados en diferentes particiones a los directorios /, /boot/, /home, /usr, /var, y /tmp

Yo siempre he usado un esquema así:

    * /swap (512 megas)
    * /root (6 a 8 gigas)
    * /home (80 gigas aprox)

Es realmente conveniente tener separados los directorios /var, /usr y /tmp? o alguno de ellos? y de ser así, que tamaño me conviene asignarles a cada una aproximadamente como para no quedarme corto, pero tampoco desperdiciar espacio???

y ésto me lleva a mi otra duda, que sistema de archivos conviene usar para cada partición???? lei en varios lados JFS es muy buena para / o para /var... y que XFS conviene con particiones de /home y archivos grandes.

Entonces se me ocurrió armar algo así:

    * /boot (ext2)
    * / (JFS)
    * /home (XFS)

Sería útil un armado así? o me conviene usar otro sistema como reiserfs, etc... y para las particiones /var, /usr y /tmp cual sería conveniente???

Y alguien a probado o conoce el JFS???

hago la consulta, ya que en todos lados que lei, la info era ya medio viejita (al menos 2 años). Asi como que casi no encontre mucho como ser reseñas del JFS.

Desde ya muchas gracias :D


PD: En todos lados dicen: que XFS es bueno para archivos grandes y que ReiserFS es bueno para pequeños. Pero que es un "archivo grande"? uno de 200mg o uno de 4gb?? y uno pequeño? uno de 1 mg o uno de 4kb????

---

### Post by hictio on 2008-12-02
Fijate en este link, hay algunos tips buenos para el esquema de particiones: [Linux Server Partitioning](http://shearer.org/Linux_Server_Partitioning)

En mi humilde opinion, la mayor parte de lo que se hace y lee en internet sobre particiones es aplicable con cuenta gotas, porque en estos ult. años hubo una revolucion de tamaños disponible en HDD comunes (amen de la virtualizacion y del LVM).
Ademas, originariamente, el tema de las particiones era fundamentalmente debido a:

- los crashes que tenia Unix
- el tamaño (poco) de los HDDs.

Estrictamente, en realidad la unica particion que no se puede hacer independiente es '/etc' que tiene que estar si o si dentro de /, porque tiene el archivo fstab con la info sobre las particiones del sistema.

Pero las particiones, son "necesarias" en un servidor en realidad, ahora, que particiones, y de que tamaño, en mi opinion no hay una respuesta standard, depende que servidor (hardware) y que funcion va a cumplir.
En lo personal, siempre me gusto la explicacion de que tamaño, y que funcion y porque es asi, tiene el manual de OpenBSD, y de FreeBSD:

- [4.7 - How much space do I need for an OpenBSD installation?](http://www.openbsd.org/faq/faq4.html#Partitioning)
- [2.6 Allocating Disk Space](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html) (Busca: Table 2-2. Partition Layout for First Disk)

Obviamente, esta info es aplicable con muchas comillas para un workstation con Ubuntu, pero no deja de ser interesante :D
Faktokrm lo dijo en un post, para un Ubuntu normal, desktop, lo mejor es:

/ - 10 GB
swap - 2 veces el RAM
/home - resto del HDD


En cuanto a los file systems, pequeños son archivos de no mas de 32 KB, era lo cosiderado el standard para un mail server, por eso tambien se lo usaba fundamentalmente en la particion /var, que es donde se almacenan los spools de emails, (entregados y por entregar).

La otra revolucion, o por lo menos, el file system que mas polvo levanto ultimamente es [zfs](http://en.wikipedia.org/wiki/Zfs).

---

### Post by Thalskarth on 2008-12-02
Le estuve pegando una ojeada a los links que me diste... me interesó el ZFS, lastima que sea incompatible con la GPL y por eso no esté en linux.

De casualidad pase por la [wiki en el ext4]("http://en.wikipedia.org/wiki/Ext4") y ahí dice que desde el pasado 11/10/2008, junto a la versión 2.6.28 del kernel linux, el ext4 a dejado de estar en development.
Por lo que ya se lo considera "estable" y final.

Alguno sabe si realmente conviene usarlo? estuve buscando info sobre él, pero nada nuevo... todo tenia ya su tiempo así que no se si sigue siendo asi.

---

### Post by MeduZa on 2008-12-02
yo para el sistema uso varias particiones y varios discos rigidos.
/ lo tengo en un disco de 80gb sata en una particion de 15gb (ext3)
swap lo tengo en el mismo disco en una particion de 2gb (swap)
/home lo tengo en otro disco de 160gb sata (ext3)
/home/music
/home/videos
/media/shared
los tengo en lo que sobra del de 80 (xfs)

antes tenia el / en raiser pero me fallo y lo deje de usar

---

### Post by hictio on 2008-12-02
Mi laptop con 8.10 la tengo con un HDD de 120 GB, con ext3, con estas particiones:

/ - 10 GB
/boot - 200 MB
swap - 1 GB
/home - Resto del HDD

Mi desktop con 8.10 la tengo con 2 HDD, uno de 6.9 GB con / en ext3; y el otro de 80 GB en /home/ con Reiserfs (para probarlo un poco).

---

### Post by MeduZa on 2008-12-07
> **hictio said:**
> Mi laptop con 8.10 la tengo con un HDD de 120 GB, con ext3, con estas particiones:

/ - 10 GB
/boot - 200 MB
swap - 1 GB
/home - Resto del HDD

Mi desktop con 8.10 la tengo con 2 HDD, uno de 6.9 GB con / en ext3; y el otro de 80 GB en /home/ con Reiserfs (para probarlo un poco).

me muero de ganas de poner el / en un disco solido de no mas de 30gb junto con la swap

---

### Post by hictio on 2008-12-07
> **MeduZa said:**
> me muero de ganas de poner el / en un disco solido de no mas de 30gb junto con la swap

A cuánto están ya?
La última vez que los vi, estaban carísimos...

---

### Post by pol666 on 2008-12-07
mira un "/" de 7gb a mi me va bien. en cuanto a swap yo uso 1gb, lo mismo que tengo de ram

---

### Post by hictio on 2008-12-07
> **pol666 said:**
> mira un "/" de 7gb a mi me va bien. en cuanto a swap yo uso 1gb, lo mismo que tengo de ram

En mis máquinas personales, hace ya unos años que tampoco le pongo 2 veces y 1/2 la cantidad de RAM como swap, me parece un desperdicio de espacio de HDD, no se...
Yo no uso ninguna aplicación de edición de video o algo asi que necesite tanto swap, usualmente el swap lo creo del mismo tamaño que la cantidad de RAM que tiene la máquina.

---

### Post by z37a on 2008-12-08
Yo generalemnte particiono asi:

/BOOT - 128MB( no mas si no se puede ensuciar mucho el sistema!)
SWAP - 2GB max(si tenes 1GB o mas lo hago de la misma cantidad, hasta los 2GB, si son 512 para abajo le meto el doble)
/ - 8GB aprox(depende el temañao del disco donde instale)
/HOME - Resto

En el caso particular de mi PC desktop, que la uso de fileserver y p2p server(por ahora):

/mnt/p2p - Toneladas de GB!!!! jajajajajaj(Tiene un RAID0 por soft de 560GB)

Si lo que queres es un arranque bien rapido del sistema usando discos solidos y bueno tendrias que poner el /BOOT y el / (o parte de el) en 2 particiones y asi andaria bien rapido!!!!

Ahora con el sistema de archivos uso EXT3, pro que, pro que no me quise romper mucho la cabeza, aanda bien, funciona rapido es una PC nueva y discos nuevos(SATA con NCQ y 16MB de buffer c/u)

---

### Post by hictio on 2008-12-10
Una muestra practica de ZFS en accion, el time Machine de Apple, tiembla :p ;)

[url=http://java.dzone.com/news/killer-feature-opensolaris-200?cid=e7711]Time Slider: OpenSolaris 2008.11 Killer Feature
[/url]

---

### Post by faktorqm on 2008-12-11
A mi me gusta este :P [http://www.dragonflybsd.org/hammer/index.shtml](http://www.dragonflybsd.org/hammer/index.shtml)

---

