---
title: "Identificacion de particion con gparted"
date: 2008-09-07
forum: Hardware
---

### Post by Kantaleon on 2008-09-07
Buenos días! 
Actualmente utilizo Kubuntu 8.04 LTS, 
Tengo un disco IDE Hitachi 80GB, no recuerdo el modelo, conectado a un mother asus P5GC-MX /1333. 
El problema es el siguiente,
Cuando hago una partición con GPARTED en lugar de tomármela como HDA1 por ejemplo me la toma como SDA1. Quisiera saber porque sucede esto, porque gparted identifica de esta manera mi disco IDE.
Cuando intento utilizar el siguiente comando para crear mi sistema de archivos: mke2fs -jv /dev/hda1 no reconoce el dispositivo, recién lo hace cuando en su lugar pongo SDA1.

Desde ya muchas gracias!

---

### Post by fmsismo on 2008-09-08
Porque se esta trabajando en los discos ide como si fueran scsi.  Se cambió la nomenglatura para estandarizar (No me acuerdo a partir de que kernel se hizo).

/dev/sda hace referencia al primer disco scsi o ide (como es tu caso).  Salvo esta diferencia no deberías encontrarte con ningún otro problema.

Saludos

---

### Post by sajnox on 2008-09-09
Este cambio entro con el Kernel que trajo Hardy

---

