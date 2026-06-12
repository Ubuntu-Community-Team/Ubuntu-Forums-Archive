---
title: "[SOLVED] Montar particion NTFS"
date: 2008-12-16
forum: Hardware
---

### Post by KG295 on 2008-12-16
Hola, tengo un problema el montar una particion ntfs, ya intente con todas las guias pero me sigue dando error, les dejo los pasos que hice para ver donde esta el problema:

1º sudo aptitude install ntfs-3g

Instalo sin ningun error

2º sudo fdisk -l

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3518    28258303+   7  HPFS/NTFS
/dev/sda2            4723        9728    40210695    f  W95 Ext'd (LBA)
/dev/sda3            3519        4722     9671130   83  Linux
/dev/sda5            4845        9728    39230698+   7  HPFS/NTFS
/dev/sda6            4723        4844      979902   82  Linux swap / Solaris

Por lo que veo de la tabla tengo que montar el sda5.

3º sudo mount -t ntfs /dev/sda5 /media/datos

La carpeta datos ya la cree.

Tira el siguiente error:

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda5': Error de entrada/salida
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

No se que mas probar, espero que me puedan ayudar, gracias.

---

### Post by staar on 2008-12-16
es un error comun, no te deja montarlo porque encuentra errores en el sistema de archivos...
te recomiendo que hagas lo siguiente

abri winbugs, anda a mi pc->click derecho en el disco->propiedades->norecuerdoquepestaña->comprobar errores o similar->tilda reparar errores automaticamente->comprobar->y listo :D

sino de la forma mas linuxera...
en win inicio->ejecutar->cmd y en la 'consola' pones ```
chkdsk X: /f
```reemplazando X por la letra de la unidad :D:D

ojo, si la unidad es la C, no va a poder bloquearla, para analizarla, y te va a preguntar si queres analizar la unidad en el proximo reinicio, dale que si y reinicia...

despues de que haya reparado los errores, anda a linux y monta la unidad :D:D:D;)

saludos

---

### Post by granjero on 2008-12-16
no trataste con el administador de discos?
ahi tenes la forma gráfica de hacerlo...

sistema/administracion/administrador de disco...


salud!

---

### Post by KG295 on 2008-12-16
Muchisimas gracias, era lo del scan disk, no pense que podia ser para tanto :p, saludos.

---

