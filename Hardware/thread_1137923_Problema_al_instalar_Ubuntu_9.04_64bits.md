---
title: "Problema al instalar Ubuntu 9.04 64bits"
date: 2009-04-26
forum: Hardware
---

### Post by qZweWfYjaz on 2009-04-26
Hola gente, soy seguidor de ubuntu desde la version 7.10 hasta ahora pero solo las probaba y luego bue ya saben jaja, ahora como lo veo mas madurito se me dio por querer pasarme totalmente, pero desde que instale la version 9.04 me va todo mal :( resulta que al activar los drivers para mi placa de video ATI HD3200 me corre todo muy lento, y lo peor es que al intentar ver un video este produce un error y me lleva directo a la pantalla de logueo de Ubuntu :shock: ??? instale tambien el ati catalyst 9.4 de la pagina oficial y tambien me pasa lo mismo, y eso solo con los efectos que trae ubuntu, al instalar el compizfusion si corria el efecto de cubo se trababa todo ni navegar por internet podia, a alguien mas le paso esto o es por mi placa grafica?, mañana voy a intentar bajar la version de 32bits a ver si me funciona mejor [-o< ...saludos!...xD...

---

### Post by clasificado on 2009-04-26
Placa de video escucho siempre que son un problema :P yo tengo la intel integrada que es una **, pero cada versión de kernel anda un poquito mas rápido

Jaunty es muy nuevo, por ahi tarden un poco en darte tu respuesta

A ver si llega alguien a darte tu respuesta milagrosa

clasificado

---

### Post by aleperno on 2009-04-26
Busque en la pag, fijate si este Driver te sirve.
Soporta entre tantos estos:
ATI RadeonTM HD 3300 Series ATI RadeonTM 3100 Series
ATI RadeonTM HD 3200 Series ATI RadeonTM 3000 Series

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

Ahi tenes un .PDF con la informacion necesaria, ademas de links con ayuda para la instalacion.

Un abrazo!

---

### Post by Hei Ku on 2009-04-26
Para Jaunty tenes que usar sí o sí el driver 9.4 de ATI. Si tenés problemas con ese (a mi me anda bien en una HD4850) vas a tener que esperar al de mayo. Es nuevito para el xorg 1.6, asi que puede ser que haya algunos bugs todavia.

---

### Post by qZweWfYjaz on 2009-04-26
Eh gracias por responder, bueno les comento, probe los drivers de ATI  v9.4 y hacia lo mismo, ahora estaba terminando de configurar el ubuntu de 32bits para ver si anda mejor en este y bue, no! :(  se pone lento cuando activo los efectos de compizfusion, con los que trae ubuntu anda maso, en la version 8.10 de ubuntu andaba mejor, hasta Vista me anda rapidisimo jajaja :P la HD3200 la tengo en una mother Asus M3A78-EMH HDMI, bue voy a tener que esperar los nuevos drivers que saque Ati, ojalan lo hagan rapido :popcorn: saludos!...xD...

---

### Post by Hei Ku on 2009-04-27
Postea el resultado del comando glxinfo

---

### Post by qZweWfYjaz on 2009-04-27
Hola nuevamente, encontre info en un blog que me sirvio, ahora anda mas fluido con compiz activado y al reproducir videos anda mejor, ahora puedo reproducir a pantalla completa sin que se reinicie el entorno grafico y me mande al logueo de nuevo, hace uno que otro parpadeo cuando el video es muy grande pero bue jeje :)

Aca dejo el link por si alguien tiene el mismo problema: [http://hp-tx2532la.blogspot.com/2009/04/ubuntu-904-jaunty-jackalope-en-la-hp.html](http://hp-tx2532la.blogspot.com/2009/04/ubuntu-904-jaunty-jackalope-en-la-hp.html)

---

### Post by euzkoarima on 2009-04-28
> **Hei Ku said:**
> Para Jaunty tenes que usar sí o sí el driver 9.4 de ATI. Si tenés problemas con ese (a mi me anda bien en una HD4850) vas a tener que esperar al de mayo. Es nuevito para el xorg 1.6, asi que puede ser que haya algunos bugs todavia.

Tengo la misma placa, pero aún 8.10
Pregunta, tenes instalado 9.04 32 o 64 bits ??

Uno de los problemas con el driver propietario de ATI es que la versión para 64 va más atrasada que la de 32

Saludos,
Eduardo

---

### Post by z37a on 2009-04-29
> **faczever said:**
> Eh gracias por responder, bueno les comento, probe los drivers de ATI  v9.4 y hacia lo mismo, ahora estaba terminando de configurar el ubuntu de 32bits para ver si anda mejor en este y bue, no! :(  se pone lento cuando activo los efectos de compizfusion, con los que trae ubuntu anda maso, en la version 8.10 de ubuntu andaba mejor, hasta Vista me anda rapidisimo jajaja :P la HD3200 la tengo en una mother Asus M3A78-EMH HDMI, bue voy a tener que esperar los nuevos drivers que saque Ati, ojalan lo hagan rapido :popcorn: saludos!...xD...

Tengo el M3A78-MN que es el mismo chipset, solo cambia en pocas cosas. Yo tuve problemas serios con el driver, lo solucione llendo a la BIOS y poniendo en Video 256Megas dedicados, me funciona de 10 ahora!!!!

---

### Post by qZweWfYjaz on 2009-04-29
Si lo tengo configurado todo bien, el problema que tenia era que al activar los efectos del compiz se volvia todo como muy pesado, lo que veo ahora es que el xorg me come mucha ram de a rato, me llega a consumir como 900mb :confused:

---

### Post by Hei Ku on 2009-04-29
> **euzkoarima said:**
> Tengo la misma placa, pero aún 8.10
Pregunta, tenes instalado 9.04 32 o 64 bits ??

Uno de los problemas con el driver propietario de ATI es que la versión para 64 va más atrasada que la de 32

Saludos,
Eduardo


Yo tengo la version de 64 bits y anda bien. Pero de hecho creo que usa casi lo mismo para las dos.

---

### Post by euzkoarima on 2009-04-29
> **Hei Ku said:**
> Yo tengo la version de 64 bits y anda bien. Pero de hecho creo que usa casi lo mismo para las dos.

Gracias, es bueno saberlo (para hacer el update más tranqui)

Saludos,
Eduardo

---

