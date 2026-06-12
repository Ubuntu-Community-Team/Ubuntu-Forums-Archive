---
title: "Como activar wifi - placa d-link dwa-525"
date: 2011-03-05
forum: Hardware
---

### Post by mano negra on 2011-03-05
Buenas,
   Hace unos días les hablé respecto de qué placa wifi poner. Finalmente le puse una d-link dwa-525. Me fijé si la reconocía, ahí les muestro lo que tiró:

:~$ lspci -nn | grep Network
04:06.0 Network controller [0280]: RaLink Device [1814:3060]

En la configuración de conexiones de red no me aparece nada respecto al wifi. pensé que por ahí tenía que instalar en driver. De la página de d-link me bajé los controladores (según ellos). El  tema es que no tengo idea de como se instala eso. Se trata de una  carpeta que contiene muchos archivos dentro. Con un .deb no tengo  problemas.
saludos

---

### Post by hectorivand on 2011-03-05
> **mano negra said:**
> Buenas,
   Hace unos días les hablé respecto de qué placa wifi poner. Finalmente le puse una d-link dwa-525. Me fijé si la reconocía, ahí les muestro lo que tiró:

:~$ lspci -nn | grep Network
04:06.0 Network controller [0280]: RaLink Device [1814:3060]

En la configuración de conexiones de red no me aparece nada respecto al wifi. pensé que por ahí tenía que instalar en driver. De la página de d-link me bajé los controladores (según ellos). El  tema es que no tengo idea de como se instala eso. Se trata de una  carpeta que contiene muchos archivos dentro. Con un .deb no tengo  problemas.
saludos

Te leventa la placa pero no te reconoce ninguna red? pregunta re estupida pero debo hacerla. Estás dentro del rango de una? la probaste en otro sistema operativo y te toma la red?

Lee el readme que seguramente hay adentro, lo más probable que lo tengas que compilar pero no te asustes, seguí las instrucciones que es no es complicado.

---

### Post by mano negra on 2011-03-06
> Te leventa la placa pero no te reconoce ninguna red?
Exacto. Bah, por lo menos cuando me fijo que tengo en el mother me lo indica. Pero no se prende la luz verde en la placa.
En otro SO no lo probé, tengo solo ubuntu instalado.

---

### Post by mano negra on 2011-03-06
estuve leyendo el readme.txt. Les muestro que dice y me saco dudas:

# compile the driver (system need install kernel-header package, should be installed by default)
> make
# install the driver to system (need "root" right)
> make install

Tengo que reinstalar el kernel-header o lo hago lo que está ahi y punto?

---

### Post by mano negra on 2011-03-06
Gente,
  he logrado el objetivo. seguí estos pasos: [www.ubuntu-es.org/node/138976](www.ubuntu-es.org/node/138976)
Superé mi temor a usar la consola. Ya hace más de un año que me metí en el mundo de linux y hay cosas que todavía temo hacer. Ya lo superaré.
gracias por todo.
salud!

---

### Post by hectorivand on 2011-03-09
Bueno, genial, me alegra que la hayas hecho funcionar. Perdón por la colgada, fin de semana largo, me fui de joda :D

Saludos
Nacho

---

