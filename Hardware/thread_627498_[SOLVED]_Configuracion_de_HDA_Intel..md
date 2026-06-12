---
title: "[SOLVED] Configuracion de HDA Intel."
date: 2007-11-30
forum: Hardware
---

### Post by margori on 2007-11-30
Estimados amigos:

Estoy al borde de dejar definitivamente a Don Windows si puede resolver este ultimo problemita.

Tengo una placa madre EliteGroup GeForce 6100SM-M, que viene con audio integrado de alta definición, según alsa, Intel HDA. La cosa es que en windows tenia un programa que determinaba es lo que hacían cada una de las salidas/entradas. Podía configurarlo como sonido 5.1 o poner dos salidas iguales y una entrada de micrófono, que es la configuración a la que quiero llegar en Ubuntu, pero no se como.

Quisieran me tiraran un dato de como llegar a esa configuracion.

He leido sobre el archivo .asoundrc, pero no encuentro un documento que me explique paso por paso como se arma ese archivo, para que sirve cada palabra en el.

Gracias.

---

### Post by valucha on 2007-11-30
[COLOR="DarkOrchid"]Hola, esa placa da varios dolores de cabeza, suerte que ahora ya hay más gente que la tiene, por ende más tutoriales y seguro que en cualquier momento sale una actualización y se soluciona.

Yo la tenía antes, pero por error, habia comprado una nueva compu y me pusieron una placa mother que yo no quería. No tenía ningun problema proque eran muy parecidas (hasta tenia mejores especificaciones de las que yo había pagado :))pero al ver lo de esta placa de sonido decidi ir a reclamar.

Hice varios cambios, la verdad no sé cuál fue el que funcionó pero al final tuve mi sonio andando correctamente.

SOLUCIONES: (son para feisty)

SOLUCIÓN 1:

[http://www.planetamd64.com/lofiversion/index.php/t23938.html](http://www.planetamd64.com/lofiversion/index.php/t23938.html) ---> [http://www.lixsystems.net/lix/support.htm](http://www.lixsystems.net/lix/support.htm) -->
SOUND:
These motherboards use intel-hda audio. Update to alsa version 1.0.11. In case you hear a high pitch sound from the speaker add the following option to modules.conf "options snd-hda-intel position_fix=1 model=3stack"        



SOLUCIÓN 2:
instalar alsaconf:
[http://ubuntuforums.org/showthread.php?t=311166&highlight=howto+alsaconf](http://ubuntuforums.org/showthread.php?t=311166&highlight=howto+alsaconf)

e instalar el driver adjunto.


Ojalá que te sirva

Pd: yo no es que no tenia sonido sino que tenia un pitido horrible. Pero es la misma placa[/COLOR]

---

### Post by margori on 2007-12-02
Gracias por el dato, pero no me sirvieron.

Aun estoy en veremos con este asunto...

---

### Post by rojojuan on 2007-12-02
Segurmante ya la hiciste, pero por las dudas: Sistema - Preferencias - Sonido y aquí podés probar con las opciones disponibles.

> **margori said:**
> Estimados amigos:

Estoy al borde de dejar definitivamente a Don Windows si puede resolver este ultimo problemita.

Tengo una placa madre EliteGroup GeForce 6100SM-M, que viene con audio integrado de alta definición, según alsa, Intel HDA. La cosa es que en windows tenia un programa que determinaba es lo que hacían cada una de las salidas/entradas. Podía configurarlo como sonido 5.1 o poner dos salidas iguales y una entrada de micrófono, que es la configuración a la que quiero llegar en Ubuntu, pero no se como.

Quisieran me tiraran un dato de como llegar a esa configuracion.

He leido sobre el archivo .asoundrc, pero no encuentro un documento que me explique paso por paso como se arma ese archivo, para que sirve cada palabra en el.

Gracias.

---

### Post by margori on 2007-12-05
Listo, me canse de divagar por la red y no  di con la solución.

Asi que no me quedo otra que hacer un reporte de bug.

[https://bugs.launchpad.net/bugs/174203]("https://bugs.launchpad.net/bugs/174203")

Por suerte o mala suerte, ha sido confirmado el problema en prioridad media. Espero pronto tener listos mis parlantes.

Gracias a todos.

---

### Post by kenoby31 on 2012-02-17
Hola a mi me funcionó lo siguiente

     

 [http://alegnalinux.blogspot.com/2012/02/sin-sonido-en-ubuntu-10x-11x-int...]("http://alegnalinux.blogspot.com/2012/02/sin-sonido-en-ubuntu-10x-11x-intel-hda.html")
 









saludos

---

