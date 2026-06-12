---
title: "Problema con pendrive de 8gb"
date: 2008-12-01
forum: Hardware
---

### Post by guisheca on 2008-12-01
Que tal comunidad, resulta que vino un amigo a llevarse un par de cosas de mi pc con su nuevo pendrive kignston data traveler de 8gb, y no pudo llevarse nada debido a que cada ves que intentaba copiar algo mas o menos grande (de unos 200mb por ejemplo) copiaba hasta exactamente 134mb y después SE DESCONECTABA SOLO!! como si sacara el pendrive de la pc, pero el pendrive obviamente permanecía allí. Lo mismo ocurría cuando intentaba copiar varios archivos chiquitos. Esto ocurrió en mi ubuntu 8.10 de 32 y de 64bits con un kernel 2.6.27 y 2.6.24 (el que trae hardy).
El tema es que al ir a su casa el no tuvo ningún problema con su pen drive, tanto con hardy como con winxp.
Googleando un poco encontré gente que le sucedía lo mismo pero ninguna solución. Leí que puede ser que mi entrada usb no se banque alimentar un pen de 8gb, pero no se si puede ser eso, con esa entrada hago cosas mas "grosas" creo yo, como poner a cargar un celu por ejemplo. Además mi pc es relativamente nueva, la compré en abril, es una amd athlon X2 4400 con 2gb de ram. Mi mother es una MSI K9AGM3-FIH.
En fin, ese es el problema que tengo, o que tiene mi amigo, no se :confused:
Saludos.

---

### Post by guillermolisi on 2008-12-01
> **guisheca said:**
> Que tal comunidad, resulta que vino un amigo a llevarse un par de cosas de mi pc con su nuevo pendrive kignston data traveler de 8gb, y no pudo llevarse nada debido a que cada ves que intentaba copiar algo mas o menos grande (de unos 200mb por ejemplo) copiaba hasta exactamente 134mb y después SE DESCONECTABA SOLO!! como si sacara el pendrive de la pc, pero el pendrive obviamente permanecía allí. Lo mismo ocurría cuando intentaba copiar varios archivos chiquitos. Esto ocurrió en mi ubuntu 8.10 de 32 y de 64bits con un kernel 2.6.27 y 2.6.24 (el que trae hardy).
El tema es que al ir a su casa el no tuvo ningún problema con su pen drive, tanto con hardy como con winxp.
Googleando un poco encontré gente que le sucedía lo mismo pero ninguna solución. Leí que puede ser que mi entrada usb no se banque alimentar un pen de 8gb, pero no se si puede ser eso, con esa entrada hago cosas mas "grosas" creo yo, como poner a cargar un celu por ejemplo. Además mi pc es relativamente nueva, la compré en abril, es una amd athlon X2 4400 con 2gb de ram. Mi mother es una MSI K9AGM3-FIH.
En fin, ese es el problema que tengo, o que tiene mi amigo, no se :confused:
Saludos.
Usaste una de las salidas frontales o tambien probaste las traseras ?
Las frontales son medias fallutas en general por causa de los cables que van de la motherboard al frente del gabinete.

Cuando lo retirabas para volverlo a colocar, estaba muy caliente despues de haber grabado esa cantidad de bytes ?

Hay un limite maximo de corriente para alimentar un dispositivo USB y si bien pareceria que el cargador de un celular consume mas que un pendrive, habria que revisar las caracteristicas de ese modelo para saber cuanto consume en realidad (como otra posible causa).

Aparte, por lo que contas, pareceria que el tema filesystem no seria, sino le hubiese fallado despues a tu amigo, cierto ? (a pesar de que no sabemos si lo uso en un conector frontal o trasero en su PC).

---

### Post by Mauro22 on 2008-12-01
Que puertos son? Los de adelante o los de atras?


Probaste con win?

---

### Post by guisheca on 2008-12-01
Al principio use las dos frontales y después mi amigo uso las traseras, en todas pasaba lo mismo (en mi pc esto).

No recuerdo si al retirarlo estaba caliente, debe ser que no, si no lo recordaría. Lo que si, cuando fallaba quedaba titilando la lucecita del pen.

Lo que olvidé contar es que cuando ocurrieron estos hechos formateé el pendrive para descartar fallas en el sistema de archivos. Lo formateé en fat32 y luego en ext3 y siempre pasaba los mismo (no se porque el gparted no me dejaba formatear en ntfs).

Le pregunté a mi amigo donde lo conectó al pen en su casa y me dijo que lo hizo en las entradas frontales y le anduvo bien tanto en win como en hardy, y lo probó copiando archivos grandes, de 700mb (pelis, incluso las reprodujo dentro del pen).
En mi pc también tengo win, pero no reparé en probarlo allí.
Saludos.

---

### Post by guillermolisi on 2008-12-01
> **guisheca said:**
> Al principio use las dos frontales y después mi amigo uso las traseras, en todas pasaba lo mismo (en mi pc esto).

No recuerdo si al retirarlo estaba caliente, debe ser que no, si no lo recordaría. Lo que si, cuando fallaba quedaba titilando la lucecita del pen.

Lo que olvidé contar es que cuando ocurrieron estos hechos formateé el pendrive para descartar fallas en el sistema de archivos. Lo formateé en fat32 y luego en ext3 y siempre pasaba los mismo (no se porque el gparted no me dejaba formatear en ntfs).

Le pregunté a mi amigo donde lo conectó al pen en su casa y me dijo que lo hizo en las entradas frontales y le anduvo bien tanto en win como en hardy, y lo probó copiando archivos grandes, de 700mb (pelis, incluso las reprodujo dentro del pen).
En mi pc también tengo win, pero no reparé en probarlo allí.
Saludos.
Con lo que acabas de decir la causa "file system" esta descartada.

Lo que se me ocurre es que la fuente de tu PC no este a la altura del consumo que requiere el pendrive, ya sea porque esta muy justa para el hardware que estas usando o porque el pendrive consume un poco mas de lo pensado (de nuevo aqui seria interesante conocer este dato sobre cuanta corriente necesita).

Habitualmente uso un Corsair de 4 Gb y un Kingston de 2Gb en dos maquinas casi iguales (la misma marca y modelo de fuente. motherboard y procesador, la misma cantidad y tamaño de discos rigidos y memoria RAM. La unica diferencia es que una tiene un placa gForce PCIExpress y la otra no) y nunca tuve problemas.

---

