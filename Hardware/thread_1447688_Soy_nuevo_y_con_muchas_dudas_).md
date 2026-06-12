---
title: "Soy nuevo y con muchas dudas :)"
date: 2010-04-05
forum: Hardware
---

### Post by Caasy on 2010-04-05
Bueno, hace poco que instale Ubuntu en mi netbook, y lo primero que pude notar es que me anda medio lento, y que no puedo acceder ni a la resolucion de la pantalla (monitor desconocido) ni a los efectos visuales..
No se como fijarme si Ubuntu instalo todos los drivers de manera correcta, pero supongo q la placa aceleradora (Intel Graphics Media Accelerator 500) no se instalo correctamente, busque en google, probe con muchos comandos y no puede lograr nada.. pido perdon si esta este tema en un post ya echo, aclare que soy nuevo y soy nuevo buscando resoluciones de problemas en linux tambien..

Muchas gracias de ante mano..

---

### Post by guillermolisi on 2010-04-05
Contanos de que netbook estamos hablando, marca y modelo de minima, y de que version de Ubuntu, asi podemos ubicarnos en situacion y aconsejarte.

---

### Post by Caasy on 2010-04-06
> **guillermolisi said:**
> Contanos de que netbook estamos hablando, marca y modelo de minima, y de que version de Ubuntu, asi podemos ubicarnos en situacion y aconsejarte.

Es una Asus 1201 ha, el ubuntu 9.10 es..

---

### Post by guillermolisi on 2010-04-06
Display: 12.1 inch, 1366 x 768 pixels (esta seria su maxima resolucion segun el manual)

He visto varios threads en Ingles en el foro, en la seccion Hardware & Laptops, referidos a esa placa de video pero de otras maquinas similares y en general hacen referencia a los paquetes psb-kernel-headers, psb-kernel-source, psb-modules, xpsb-glx libdrm-poulsbo1, poulsbo-config psb-firmware que estan en repositorios personales (ppa).
Inclusive han hecho funcionar Compiz (efectos) con exito.

Por si te arreglas con el Ingles, te recomiendo leer estos threads:

[http://ubuntuforums.org/showthread.php?t=1378746](http://ubuntuforums.org/showthread.php?t=1378746)
[http://ubuntuforums.org/showthread.php?t=1408276](http://ubuntuforums.org/showthread.php?t=1408276)

Hay mas pero con estos tenes para entrenerte. No vi una solucion "facil".

Fijate que casi siempre hacen referencia a la version de kernel que estan usando.

Si queres saber que version de kernel tenes en uso ingresa, en una terminal/consola, este comando: ```
uname -a
``` y entre los datos que te devuelve estara la version del kernel en uso.

---

