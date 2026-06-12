---
title: "[SOLVED] Problema para instalar ubuntu en mi Toshiba Satellite A60"
date: 2008-07-19
forum: Hardware
---

### Post by ctalamochito on 2008-07-19
Gente, soy absolutamente nuevo en todo el ubuntu, pero he visto algo y lo quería instalar en mi notebook para probarlo y tal vez olvidarme de una vez por todas del "ventanas", perome surgieron algunos problemas:
Trato de instalar el ubuntu 8.04.1 desktop i386, pero no puedo.
Lo intenté en dos opciones: 1- instalarlo desde windows, pero al finalizar la creación de imagen, me salt aun error porque alguna aplicación utiliza mi lectora de CD, lo cual no se como solucionarlo.
                            2- lo intento instalar mediante la reiniciación de mi máquina, pero me sale el siguiente error, luego de un rato: "Busy Box v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
             Enter ´help´ for a list of built-in command"

Eso la verdad que no lo entiendo e intenté solucionarlo, pero no logré nada, me empezaron a salir errores miles (SQUASHFS), con lo que más perdido quedé.
Ahora les paso las especificaciones de mi máquina:

Toshiba Satellite
Intel Celeron CPU 2.66 GHz
2,67 GHz, 1,12 GB RAM

Video: ATI Radeon 7000 (128 Mb)
HD: SATA 30 Gb

Espero puedan ayudarme, muchas gracias.

Diego.

---

### Post by atari130xe on 2008-07-19
a ver si te sirve este link: 

[http://www.yoreparo.com/nav/?url=http://www.ubuntu-es.org/index.php?q=node/86409]("http://www.yoreparo.com/nav/?url=http://www.ubuntu-es.org/index.php?q=node/86409")

---

### Post by ctalamochito on 2008-07-20
Gracias che, voy a ver si puedo instalarlo de esa forma, cualquier cosa vuelvo con más preguntas.

---

### Post by ctalamochito on 2008-07-28
No che, no he podido...
Tal vez porque no tengo mucha idea.
Pero bueno, veré como lo soluciono.

---

### Post by Tosh78 on 2008-07-29
El error del windows cuando lo instalas con wubi lo vi un par de veces. Eso, en los casos en que lo vi, se soluciono desfragmentando el disco ANTES de intentar instalar ubuntu. Fijate si haciendo eso y volviendo a instalarlo te funciona. El otro error nunca lo vi, pero podes probar con el alternate cd.

---

### Post by arleneteng on 2008-07-31
Ahora he acabado de instalar Ubuntu en mi Toshiba Satellite A60 usando wubi y no tenía ningunos problemas. Era aprisa y muy fácil. :KS

---

### Post by jualin on 2008-07-31
El error de BusyBox es muy comun en instalaciones Wubi. Para solucionar ese problema debes cambiar las lineas de buteo (spanglish). Debes quitar la parte de "Quiet Splash" y corregirla con "all_generic_ide". Pero tienes que tener a Ubuntu instalado para tener este error o para solucionarlo :lol:.

---

### Post by ctalamochito on 2008-08-01
Bueno, al final era una solución muy simple, tenía un desastre mi disco, asique formateé la máquina instalando todo lo original, luego defragmenté el disco y ahí arrancó sin problemas, ahora solo me queda formatear nuevamente para que las particiones tengan la capacidad de instalar el Ubuntu...
Muchas gracias...

---

### Post by jualin on 2008-08-01
No hay problema, que bueno que resolviste tu problema!

---

### Post by Tosh78 on 2008-08-05
Me alegro de que lo hayas resuelto. Saludos!

---

