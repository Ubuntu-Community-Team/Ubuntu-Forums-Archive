---
title: "Boteo dual, poner windows en grub"
date: 2009-05-18
forum: Instalación y Actualización
---

### Post by vampireline on 2009-05-18
Hola....que bueno que volvió este foro..

mi tema es este, hace un tiempo usaba Ubuntu, después lo deje por problemas de disco por windows...hace unas semanas que  instale Ubuntu 9.04 en un disco IDE de 40gb que encontre en el closet(?) pero ya tenia windows xp en otro IDE de 40gb..entoces no pude hacer que en el Grub no salga windows en la lista de S.O.

como puedo hacer para que aparesca en el grub?...ojala sin reinstalar Ubuntu ni tocar windows.

tengo otro disco SATA de 120gb pero ese es de solo datos, el S.O. windows esta en el IDE.

Saludos y ojala me puedan ayudar.

---

### Post by moreback on 2009-05-18
La entrada estándar para un Windows es como la que sigue:

```
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```En lo anterior debieras modificar la línea de dice** root (hd0,0)** por la que corresponda a tu disco duro. Podría ser algo como (hd1,0) o (hd2,0) pero para eso necesitamos saber como están estructurados tus discos.

Saludos.

---

### Post by vampireline on 2009-05-18
Si, eso hay que editarlo el archivo menu.lst no?...

Pero encuentro algo raro, porque según tengo entendido los discos IDE los reconoce asi: hd0, hd1, etc...pero si pongo el comando "fdisk -l " (que es para ver las particiones) me sale esto:

[I]Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x58425842

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       14592    76252522+   f  W95 Ext'd (LBA)
/dev/sda5            5100       14592    76252491    7  HPFS/NTFS

Disco /dev/sdb: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x153d153c

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extendida
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris

Disco /dev/sdc: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8524ec79

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1        2040    16386268+   7  HPFS/NTFS
/dev/sdc2            2041        4865    22691812+   f  W95 Ext'd (LBA)
/dev/sdc5            2041        4865    22691781    7  HPFS/NTFS[/I]     

En todos salen sda o sdb...que según tengo entendido es la sigla de los discos sata...
Igual podría poner (sda,1) para windows?...en que parte del archivo lo coloco?..
al final?.

los disco yo tengo 2 ide, en el primero esta Ubuntu(maestro) y en el otro conector del cable esta el disco con windows(2 particiones).....aparte tengo un SATA que tiene archivos en windows(2 particones)

saludos.

---

### Post by Patriciologico on 2009-05-18
Ojo, La nomenclatura que usa grub ej (hd0,0) no es la misma de fstab
puedes leer por ej 

[http://mortrak.wordpress.com/category/grub/](http://mortrak.wordpress.com/category/grub/)

Ademas hace unas distribuciones atras (¿7.10?) los discos ides se reconocen como sda, sdb, etc. No conozco el motivo, pero no hay problema con eso. Junto con esto los discos pasan a tener un UUID , que es un identificador unico con un numero extenso. 

ver [http://dalealteclado.com/2007/11/uso-de-uuid-en-etcfstab-y-en-grub.html](http://dalealteclado.com/2007/11/uso-de-uuid-en-etcfstab-y-en-grub.html)

En nomenclatura grub (Hd0,0) el primer numero representa la letra (a=0, b=1) y la segunda al numero de particion -1 (por ejemplo hda1 = Hd0,0)

En las versiones anteriores, te habria dicho con seguridad que en el grub debieras poner Hd0,0 , pero dado el actual uso de los UUID, me queda la duda.

Espero haberte dado algo de informacion y alguien mas puesto en el tema, te da la ayuda final.

Saludos!

---

### Post by Carlos C on 2009-05-18
> Igual podría poner (sda,1) para windows?
Creo que no, debes ponerlo como te dice moreback. Yo tengo un computador con discos SATA y mi menu.lst está exactamente así (hd0,0). Los números dentro del paréntesis se relacionan con el disco y la partición. En la [Guía Ubuntu]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Usando_una_distribuci.C3.B3n_Live") dice:
>     *  hd0: es el primero disco duro completo, al igual que hda o sda
    * hd0,0: es la primera partición del primer disco duro, al igual que hda1 o sda1
    * hd0,1: es la segunda partición del primer disco duro, al igual que hda2 o sda2
    * hd1,2: es la tercera partición del segundo disco duro, al igual que hdb3 o sdb3 

En general la información de Windows se añade al final.

EDITADO: UPS Patriciologico me ganó jajaja.

---

### Post by Patriciologico on 2009-05-18
A mi respuesta le faltaba una confirmacion ;)

---

### Post by moreback on 2009-05-18
Para saber que disco usar, usa Grub para encontrar el archivo menu.lst

```
sudo grub
find /boot/grub/menu.lst
```

La respuesta a ese comando te dirá donde se ubica el archivo y te servirá para usarlo en el comando root que te decía anteriormente.

Saludos.

---

