---
title: "Problema GRUB con un recovery Disc"
date: 2009-11-04
forum: Instalación y Actualización
---

### Post by Fabiantronc on 2009-11-04
Hola.

Tengo el siguiente problema.
Tengo un PC Lenovo de escritorio que venia con Windows XP.
Le instale Ubuntu 9.04. Ya hasta aqui todo bien.
El problema surge al querer entrar a Windows XP ya que me sale la pantalla de "recovery disc" o algo por el estilo, la cosa es que detecta que el Windows XP esta corrupto y lo instala de nuevo, como venia de fabrica.
Al instalar todo XP de nuevo no me sale el GRUB y tengo que poner el LiveCD para recuperarlo.

Es un problema ya que no puedo entrar a XP sin reinstalarlo de nuevo (de fabrica) y no puedo instalar ubuntu ya que por alguna razon no bootea de la particion de XP.

Tengo un disco duro de 250 GB :
- 100 GB (aprox.) para la particion donde esta Windows XP.
- 100 GB (aprox.) para la particion de Ubuntu.
- 500 MB creo(?) de area de intercambio.
- 4 GB en una unidad FAT32 donde esta el disco de recuperacion (viene de fabrica.)

El PC tiene un Core2Duo de 2.6 Ghz y 3 GB RAM.

No lo puedo dejar todo con Ubuntu ya que es del trabajo y tampoco todo con XP ya que estoy trabajando con PHP y Mysql

Chau.

---

### Post by ClarkXP on 2009-11-04
Haber dejame entender, cuantas particiones tiene tu pc???

con ubuntu o un livecd podrias darnos lo que te sale ejecutando
```
$ sudo fdisk -l
```

a mi parecer no es que windows este dañado sino que grub tomo la particion de recuperacion de sistema (donde incluye todo para restaurar ese horroroso sistema) como "la particion de windows", en ese caso habría que solo modificar el archivo de conf de grub.

si quiere tambien puedes probar con:

```
$ sudo update-grub
``` 
PD: si es grub2 el comando es update-grub2

---

### Post by Fabiantronc on 2009-11-05
El disco duro venia con 2 particiones, 1 NTFS con Windows XP y otra FAT con el recovery disc.
Luego saque 100 GB de la particion de Win XP para instalar Ubuntu.

sudo fdisk -l
```
Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2d58cbce

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1       15002   120503533+   7  HPFS/NTFS
/dev/sda2   *       15003       15541     4329517+  12  Compaq diagnostics
/dev/sda3           15542       30401   119362950    5  Extendida
/dev/sda5           15542       30337   118848838+  83  Linux
/dev/sda6           30338       30401      514048+  82  Linux swap / Solaris

```

sudo update-grub
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

---

