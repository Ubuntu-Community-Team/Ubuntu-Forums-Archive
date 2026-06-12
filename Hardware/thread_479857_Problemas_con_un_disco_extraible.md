---
title: "Problemas con un disco extraible"
date: 2007-06-20
forum: Hardware
---

### Post by Aswang on 2007-06-20
Hola, soy nuevo con el KDE y no se como hacer para hacer que me reconozca un disco extraíble. Alguno que me pueda ayudar porfavor que ahí tengo muchos documentos importantes.

---

### Post by guillermolisi on 2007-06-20
Aswang

Podrias especificar que tecnologia usa el disco para conectarse a la PC ? SCSI, USB, SATA, parallel, etc. ?

Que version de Ubuntu y KDE estas usando ?

---

### Post by Aswang on 2007-06-20
> **guillermolisi said:**
> Aswang

Podrias especificar que tecnologia usa el disco para conectarse a la PC ? SCSI, USB, SATA, parallel, etc. ?

Que version de Ubuntu y KDE estas usando ?

Uso el KDE y es Usb el disco, es que formatie y ahi tenia todo lo que guarde antes de formatiar. Ya probe agregando con la Konsole y no me deja :S.

---

### Post by odiseo77 on 2007-06-20
Hola, no he entendido muy bien, pero si es una unidad USB extraible como un pendrive, ubuntu debería montártela automáticamente al conectarla al puerto USB (a menos que estés usando una versión muy anticuada de Ubuntu); ¿así que supongo estás usando un disco duro USB?... Nunca he usado uno, pero si este es el caso, puedes ejecutar ***sudo fdisk -l*** después de conectarlo para ver con cuál dispositivo está asociado en /dev, luego creas el punto de montaje para el disco en /media o /mnt (preferiblemente en /media), y lo montas con ***sudo mount /dev/DISCO_USB /media/PTO_DE_MONTAJE***. Tambiés puedes revisar el directorio /media unos segundos después de conectar el disco a ver si en efecto, está montado (quizás (K)Ubuntu te lo monta, pero KDE no te lo muestra en el escritorio (no estoy muy familiarizado con KDE).

Saludos.

---

### Post by guillermolisi on 2007-06-20
Yo uso KDE desde que empece a usar Ubuntu y nunca tuve problemas para los dispositivos USB, ni con la 6.10 ni con la 7.04.

No uso discos pero si pendrives y los ve al toque, los monta solos y los desmonta sin problemas. En principio te diria que para el SO da lo mismo un HD que un pendrive USB.

Estuve viendo mi /etc/fstab y no encontre ninguna entrada referida al USB, por lo que asumo no veo problema en montarlo a mano, tal como te comento Odiseo77.

Mi recomendacion es hacerlo abriendo una consola.
.
Algo que no te pregunte y puede ser definitorio, el HD USB esta formateado con que file system, NTFS, FAT, etc. ?

---

### Post by guillermolisi on 2007-06-20
Coloque un pendrive y en mi Ubuntu con KDE y lo monta asi:
```

mount /dev/sdb1 /media/disk

```

Si no hay algo raro, deberias poder hacerlo sin necesidad de "sudo" o similar para elevar privilegios de usuario.

Para no tener problemas con el formato o tipo de file system del pendrive, lo uso siempre como FAT (o VFAT). Asi me da lo mismo Güindous o Linux.

---

### Post by Aswang on 2007-06-21
Ok, thx por la info voy a probar :)

---

### Post by Al_maverick on 2007-06-22
> **Aswang said:**
> Ok, thx por la info voy a probar :)

Si es un HD, fijate en que formato esta, FAT32 o NTFS. Si esta en formato NTFS, Kubuntu probablemente no lo monte automaticamente a menos que tengas instalado el paquete de ntfs. Ese lo podes instalar a traves de Adept.

En mi experiencia, con conectarlo simplemente deberia reconocerlo.

Si no, podes poner en la consola tail -f /var/log/messages cuando pones el disco. Eso te va a mostrar los mensajes cuando kubuntu reconozca el usb, y probablemente te diga como que unidad lo reconozca, en general sda1, sdb1 o algo asi. Despues podes usar mount para montar el disco manualmente.

---

### Post by centro11 on 2011-08-01
La unica vez que tuve un problema asi, fue cuando necesite llamar a una empresa de nombre Onretrieval para que me recuperara los datos de un pendrive. 
 
Normalmente si no tiene problemas fisicos, cualquier dispositivo tiene la posibilidad de recuperarsele los datos. Siempre que se sepa como hacerlo, claro...
 
Hoy en dia existen dispositivos mas seguros como, por ej, los discos solidos o discos SSD.
 
Son mas caros pero si se precisa seguridad, son la solucion-
 
Saludos.

---

### Post by guillermolisi on 2011-08-01
> **centro11 said:**
> La unica vez que tuve un problema asi, fue cuando necesite llamar a una empresa de nombre Onretrieval para que me recuperara los datos de un pendrive. 
 
Normalmente si no tiene problemas fisicos, cualquier dispositivo tiene la posibilidad de recuperarsele los datos. Siempre que se sepa como hacerlo, claro...
 
Hoy en dia existen dispositivos mas seguros como, por ej, los discos solidos o discos SSD.
 
Son mas caros pero si se precisa seguridad, son la solucion-
 
Saludos.
Claro, del 2007 al 2011 han cambiado muchas cosas, entre ellas la tecnologia y los precios :P

---

