---
title: "Ubuntu 9.04 server con raid 1"
date: 2009-07-30
forum: Hardware
---

### Post by Diego.Barragan on 2009-07-30
Hola,
       Soy nuevo en el foro y como casi cualquier nuevo, tengo una duda! Necesito instalar Ubuntu 9.04 server en un servidor HP Proliant D380 G5 con controladora raid, con 6 discos ssd hotswap, etc. Les comento que buscando en internet me encontre con varias paginas que hablan de un "fakeraid" que creo yo que se refiere a hacer un raid por software. 
       Como yo tengo una controladora raid, necesito instalar ubuntu y configurar la controladora de raid, o sea, hacer un "trueraid". Hay algun thread ya hecho con las instrucciones para hacer esto?
       Desde ya les pido disculpas si esto ya esta respondido en otro thread. Gracias por adelantado!!


Diego Barragan.

---

### Post by guillermolisi on 2009-07-30
Por que queres poner en marcha un server con esa version no LTS (Long Term Support) cuando esta la 8.04 y en Abril del año que viene sale la nueva ?

Las ediciones LTS son las mas aconsejables para servidores en produccion porque su termino de vida es muy superior al de las ediciones standard (hablando de soporte).

Fuera de eso, en el trabajo tenemos un equipo similar pero G3 o G4, tambien con 6 discos HP/Seagate de 70Gb en RAID pero con RedHat EL 4. Fue el primer server con Linux que pusimos en marcha.

Si los drivers de la controladora SCSI del equipo funcionan en Ubuntu/Debian, tranquilamente vas a poder hacer True Raid del nivel que quieras. Si los drivers no funcionan o no existen para Ubuntu/Debian ... soft raid es la unica alternativa que te queda pero olvidate del hotswap y de la administracion remota de la controladora ya que no intervendra en lo mas minimo en la gestion RAID del sistema.

Nunca probamos iniciar ese equipo con Ubuntu porque es el servidor mas critico de la empresa y no para nunca (salvo que se corte la luz, se acaben las baterias de la UPS y se consuma el combustible del motogenerador con lo cual tampoco podriamos probar nada).

En definitiva, la definicion esta en los drivers de la controladora SCSI del server.

---

### Post by fmsismo on 2009-07-31
Tenes que configurar la controladora raid de tu equipo para que haga un raid con los discos (fijate si tu controladora soportar hacer raid 10 o raid5, vas a tener un poco más de desempeño aparte de la redundancia, raid 1 por lo general se hace cuando se tiene solo 2 discos).  

Lo que leíste es de las controladoras raid que traen los equipos domesticos o servidores de gama baja (que vienen con mothers de power desktop o entry point server).  No es tu caso (o no debería serlo).  

Cuanto termines de configurar la controladora RAID el sistema va a ver el arreglo RAID como un solo disco (no 6 unidades distintas).

---

### Post by Diego.Barragan on 2009-07-31
Gracias por responder! les comento que mi jefe me pidio que bajara la ultima version de ubuntu server y la instale en este servidor, pero voy a ver si lo convenso de usar la 8.04 lts, por lo menos hasta abril del 2013. Voy a buscar los controladores para la controladora HP Smart Array E200, me parece que esta complicado que ande bien en linux por un par de paginas que vi y decian tener muchos problemas mas que nada en la velocidad de escritura de los discos. Ah, segun lei la E200 soporta RAID 0, 1 y 10. Ustedes saben si esta controladora va bien con ubuntu? o con linux en general?

gracias! saludos.


Diego.Barragan

---

### Post by fmsismo on 2009-07-31
Diego es recomendable usar 8.04 LTS si vas a poner un servidor en producción.  Pero puede que necesites usar tomcat6 o alguna de las cualidades que se incorporaron en 9.04 y no estén en 8.04.

Por lo general las versiones intermedias entre las LTS son utilizadas para entornos de prueba (de tecnología).  Ya que no es recomendable tomarse el trabajo de poner un servidor en marcha y después estar migrandolo a cada rato (Por eso es tan importante la versión LTS cuando hablas de servidores).

No vi información formal sobre esta placa de HP y Ubuntu.  Tendrías que hacer pruebas.  Leí en los fotos información dispar, gente que le andaba bien y otros que tenían problemas de performance.

Saludos

---

### Post by guillermolisi on 2009-07-31
> **Diego.Barragan said:**
> Gracias por responder! les comento que mi jefe me pidio que bajara la ultima version de ubuntu server y la instale en este servidor, pero voy a ver si lo convenso de usar la 8.04 lts, por lo menos hasta abril del 2013. Voy a buscar los controladores para la controladora HP Smart Array E200, me parece que esta complicado que ande bien en linux por un par de paginas que vi y decian tener muchos problemas mas que nada en la velocidad de escritura de los discos. Ah, segun lei la E200 soporta RAID 0, 1 y 10. Ustedes saben si esta controladora va bien con ubuntu? o con linux en general?

gracias! saludos.


Diego.Barragan
En el site de HP no estan los drivers Linux para esa controladora ? Generalmente brindan rpms ya que RedHat certifico con ellos.

Si los probas primero vas a tener que convertirlos con alien y despues luchar con las dependencias (si hay alguna no resuelta).

---

### Post by Diego.Barragan on 2009-08-06
Bueno, como en hp no estaban los controladores directamente hechos para ubuntu y si para debian, entonces mi jefe decidio instalar debian, :-/ asi que no creo que prolongue mas este post, les comento que ahora estoy peleando con la configuracion del raid 1 previa a la instalacion de debian y bue, sigo en la lucha. Gente gracias por la ayuda desinteresada!

Saludos!


Diego.Barragan

---

### Post by guillermolisi on 2009-08-06
> **Diego.Barragan said:**
> Bueno, como en hp no estaban los controladores directamente hechos para ubuntu y si para debian, entonces mi jefe decidio instalar debian, :-/ asi que no creo que prolongue mas este post, les comento que ahora estoy peleando con la configuracion del raid 1 previa a la instalacion de debian y bue, sigo en la lucha. Gente gracias por la ayuda desinteresada!

Saludos!


Diego.Barragan
Sabe tu jefe que Ubuntu esta basado en Debian y hasta comparten el upstream de desarrollo ?

Si van a probar con Debian, por que no probar antes con Ubuntu ?
Los paquetes son .deb, asi que van tanto en una como otra distribucion.

Anyway, it's up to you. Good luck.

---

