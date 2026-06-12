---
title: "Instale ubuntu y no puedo ver disco duro de respaldo."
date: 2009-10-27
forum: Instalación y Actualización
---

### Post by vampireline on 2009-10-27
Hola, les cuento mi situacion a ver si me pueden ayudar, ayer instale ubuntu en mi duco duro IDE de 0gb, antiguamente tenia windows alli. Ademas tengo un disco duro de 120gb SATA con 2 particiones ntsc con toda mi informacion y datos, pero por alguna razon no lo puedo ver desde ubuntu, es como si no estuviera conectado.
Porbe instalando el virtualbox y cree una maquina virtual de windows xp y nada, tampoco lo puedo ver.

que puede ser??

gracias, saludos.

---

### Post by Carlos C on 2009-10-28
qúe aparece si escribes:
```
sudo fdisk -l
```
¿Qué te muestra gparted?

---

### Post by vampireline on 2009-10-28
el 
fdisk -ly me sale esto...

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8524ec79

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extendida
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

por lo que se ve reconoce solo el disco duro IDE. el sata no sale, pero revise en la BIOS y si esta, sale para bootear y todo,  o sea conectado bien esta...no se como hacer para que ubuntu lo reconozca.

en el gparted tambine sale como si estuviera solo 1 disco duro(el de 40gb IDE).

[[IMG]http://img688.imageshack.us/img688/1265/sinnombre.th.jpg[/IMG]](http://img688.imageshack.us/i/sinnombre.jpg/)

---

### Post by Carlos C on 2009-10-30
Creo que el problema es la manera como conectaste los discos. Fíjate cuál está como master y cuál como esclavo. Si existe la posibilidad de que estén configurados los pines para que la selección se haga por cable, entonces mira el orden en que los conectaste al cable IDE (esto en caso de que ambos compartan el mismo cable). Yo verificaría que el cable está bueno (cambiándolo), que el orden de los discos sea el correcto y que los pines estén bien puestos. Si únicamente tienes el disco sata conectado ¿Funciona?

Saludos.

---

