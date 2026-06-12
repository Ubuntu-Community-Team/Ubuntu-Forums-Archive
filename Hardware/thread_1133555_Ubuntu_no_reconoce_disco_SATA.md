---
title: "Ubuntu no reconoce disco SATA"
date: 2009-04-23
forum: Hardware
---

### Post by KG295 on 2009-04-23
Hola, tengo un problema que no puedo resolver a pesar de mirar por todos lados otros post que tienen algo parecido, el problema es este, agregue un disco Sata (160gb) a mi pc, la cual tiene un disco ide (80gb) donde tengo una particion de linux y una de windows, primero se reiniciaba el sistema sin pasar el post, era porque faltaba el jumper para pasar de sata2 a sata1, ahora que eso ya esta tengo el problema de que una vez iniciado ubuntu el disco aparece como "unidad scsi" y no me deja montarlo, use el fdisk y me aparece esto:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x27af27ae

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3518    28258303+   7  HPFS/NTFS
/dev/sda2            4723        9728    40210695    f  W95 Ext'd (LBA)
/dev/sda3            3519        4722     9671130   83  Linux
/dev/sda5            4845        9728    39230698+   7  HPFS/NTFS
/dev/sda6            4723        4844      979902   82  Linux swap / Solaris

Por lo que veo aca esto es solamente lo del disco ide, ni noticias del sata, alguna solucion?, gracias.

---

