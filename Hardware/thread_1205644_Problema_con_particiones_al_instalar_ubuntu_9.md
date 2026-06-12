---
title: "Problema con particiones al instalar ubuntu 9"
date: 2009-07-06
forum: Hardware
---

### Post by incu2k on 2009-07-06
Hola soy un usuario nuevo y estoy intentando instalar Ubuntu Jaunty en mi XPS 1330 (DELL).
Puedo ejecutar el LiveCD y funciona todo perfecto!
Puedo ver las particiones de mi dísco y montarlas sin problemas.
El problema viene a la hora de instalar el Ubuntu. Cuando llego al paso en que debo indicar la partición en la que quiero instalarlo, me dice que mi equipo no tiene ningún sistema operativo y la tabla de particiones me aparece vacía (como si no hubiera particiones). Pero de hecho tengo 3 particiones. 
1 para Windows (hasta que logre dejar funcionando correctamente Ubuntu)
1 libre para Ununtu
1 con mis documentos, música, etc.
 
¿Qué puede estar ocurriendo?
 
muchas gracias y saludos

---

### Post by pizza-is-good on 2009-07-06
La verdad es que no se que es lo que puede estar pasando...
 
Yo empeze con Ubuntu 8.10, y al instalar cree la particion nueva. El instalador de Ubuntu me creo una particion del tamaño que yo queria, en ext3.
¿Que formato tiene tu particion para Ubuntu? ¿Y como creaste la particion para ubuntu?
 
Tambien me gustaria saber que disco duro tienes, y todas las especificaciones de tu computadora. Teniendo eso podria empezar a ayudar.
 
Yo no soy un usuario muy avanzado, pero si quieres, podria traducir tu pregunta al ingles, y ahi seguro que mas gente puede ayudar.

---

### Post by Dysport on 2009-07-06
Your problem is you don't see any partitions in the partitioner during the installation process although there should be three of them; did I get that right?

It's possible that your partition table is broken. Open a terminal, type ```
sudo fdisk -l
``` and post the output here.
Further you could check whether you see the correct partitioning layout in Gparted (Terminal: "gksu gparted").

---

