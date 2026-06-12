---
title: "AYUDA! urgente! - Arranque del sistema"
date: 2008-10-31
forum: Hardware
---

### Post by juanpedro90 on 2008-10-31
hola.. les cuento:

ayer me baje la ultima version de ubuntu (8.10) y resulta que cuando quiero bootear desde la imagen del cd me dice "Starting Bluetooth" y se me queda colgado (no tengo ningun dispositivo bluetooth).. ah y tampoco me carga los drivers del mouse.. que podra ser?

desde ya, muchas gracias

---

### Post by BlackHero on 2008-10-31
Mira generalmente las live cd no pueden cargar todo digamoslo asi mas facil


te recomiendo que instales directamente el sistema desde el cd


o si es que tenes una version anterior de ubuntu abras una consola  y tipees

sudo aptitude update
sudo aptitude upgrade



dale Y y listo se te actualiza el sistema hasta la ultima version de los repositorios =)

---

### Post by zeroadrenaline on 2008-10-31
La verdad no es muy comun , o al menos yo no lei nunca algo similar...................NAAAAAAAAAAAAA MENTIRA!!!.
Solo para sacarte la duda, cuando booteas el cd, hay una opcion que es para probar si el CD esta bien grabado, y revisa todo el disquito, si queres corre esa opcion para estar seguro.
Por otro lado tmb podes probar con otro live cd de otra distro, a ver si te tira los mismos errores, probablemente lo que pase es que ese live te este jugando una mala pasada, yo tengo algunos live cd de la muerte en casa que los tengo identificados, algunos se ganaron el mote de DE LA MUERTE solo porque mientras los usaba me mande algunas macanas, y solo por cabala, los deje de lado, pero probate uno o dos mas, te diria de Hardy, o de Ibex pero Kubuntu, o Xubuntu a ver si te pasa lo mismo, si no te pasa, yo desconfiaria del live cd ese, de ultima bajate otra iso, preferentemente oficial, y grabatela de nuevo. No graves la misma porque probablemente el error este en la iso que tenes.
Ojala soluciones. Lo mio es solo una sujerencia. Un abrazo.
PAZ!

---

### Post by juanpedro90 on 2008-10-31
recien me baje la version 32bit y me tira los mismos errores.. Antes tenia la Hardy y me andaba de 10. Podra ser algun problema de hardware? tengo un mother asus p5gc-mx/1333, disco sata de 80gb, 1gb de ram, micro pentium4 2.66ghz... ¿que dicen?

---

### Post by juanpedro90 on 2008-10-31
Saludos desde ubuntu:) jaja

pude encontrar el problema.. es el modem (Speedtouch 330) que me cuelga la maquina en el arranque.. todavia no se como arreglarlo.. si alguien tiene alguna idea, bienvenida sea

---

### Post by sam_award on 2008-10-31
mira BlackHero y zeroadrenaline ya te dieron parte de la solucion , corre el live cd y verificalo , ahi hay una opsion q dice verificar disco , y si te sale todo correcto pues hai hay un conflicto de sofware 

pero muy aparte para q quieres instalar el ibex aparte , mejor xq no mejor te actualizas el hardy a ibex y ya?

bueno ojala y encuentres solucion a tu problema aqui hay otro post q te puede sevir jejeje

[http://ubuntuforums.org/showthread.php?t=964197](http://ubuntuforums.org/showthread.php?t=964197)

ojala y te sirva , no te olvides de dar las gracias si te sirvieron las soluciones y si es asi marac solved

bueno salu2

---

### Post by acade07 on 2008-11-04
Lo q dice juanpedro90 es un bug reportado en [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291351) 
de incompatibilidad con este modem q tambien poseo yo
Fijate q mas abajo hay un archivo q tine q ser remmplazado en ubuntu.
Te recomiendo q leas esta pagina...
[http://tobal.cymaho.com/?p=476](http://tobal.cymaho.com/?p=476)
ahi explican como hacerlo.
Saludos. Ojala lo soluciones
NOTA: El archivo q se debe dercargar y reemplazar es este:  [http://launchpadlibrarian.net/19200501/speedtch.ko.tar.bz2](http://launchpadlibrarian.net/19200501/speedtch.ko.tar.bz2)
NO el del blog.

---

