---
title: "Ubuntu y drivers de video"
date: 2009-01-23
forum: Hardware
---

### Post by alexil on 2009-01-23
Hola gente, los otros dias instale Ubuntu 8.10, fue todo barbaro, con execpcion de la placa de video, no es que no funcione lo que pasa que no me pone todas las resoluciones posibles, tengo una VIA/S3G UniChrome Pro IGP onboard y un monitor de 17" cuando usaba windows tenia seteado el display en 1280x1024, ahora en ubuntu la resolucion maxima que me permite es 1024x768.

Lo que me parece a mi es que ubuntu instalo un controlador generico, por eso no puedo acceder a mas resolucion, la pregunta es como puedo acceder a mas resolucion, que archivo tengo que modificar o que programa tengo que correr.

Hace muchisimos años use Linux y me acuerdo que habia un programa que se llamaba XF86Setup o algo asi.

Muchas gracias en avanzado

---

### Post by Hei Ku on 2009-01-24
Tenes el driver OpenChrome, que a veces da buen resultado. Y tambien fijate en la pagina de VIA, que estaban liberando sus drivers y capaz tenes algo para tu placa.

Ahora haces todo a traves del xorg.conf.

---

### Post by guillermolisi on 2009-01-26
Esas placas de Via no tienen aceleracion 3D (tengo dos y en una maquina termine colocando una GForce 6200 para cortarla con los problemas de video y tener aceleracion grafica completa).

Via no le da mucha bola a Linux, solamente como para cumplir, pero limitadamente, por lo menos por ahora.

---

