---
title: "Solucion para Commodore KE8390 o cualquiera con problemas d ACPI o Bios"
date: 2009-04-27
forum: Hardware
---

### Post by LuisTuc on 2009-04-27
la verdad me habia kedado muy frustrado despues d no poder haber instalado ubuntu 8.10 durante la FLISoL 2009 y mas tarde la Realse Party d 9.04, asi q hoy mientras buscaba una solucion para poder hacer andar mi modem 3g en ubuntu 8.04, me molesto mucho ver q la version tenia muchissimos problemas con mucho del harware d mi notebook, asi q me puse las pilas y dije... "no paro hasta q no tenga 8.10 andando" y me puse a probar.
Tanto sera mi toketeo q lo Logre!! logre instalarle Kubuntu 8.10 Intrepid Ibex en mi maquina! despues d haber estado cerca d 2 horas con los chicos el sabado a la noche en Tazz, era lo q todos pensaban: Un problema con la placa integrada Via! sumado a obviamente una Bios desactualizada, y d bajo calibre como lo son las PhoenixAward q tiene problemas con el ACPI

la solucion es la Siguiente:

Cuando van a elegir q opcion d instalacion quieren aprietan "F6" para editar las opciones

[IMG]http://incqre.net/img/inst2.png[/IMG]

agregamos a la linea d comandos las siguientes opciones: 

*noapic nolapic irqpoll*


y por ultimo pero no menos importante presionamos "F4" y ponemos *_**"Modo Grafico Seguro"**_* este paso es escencial ya q sin esto no c puede ver nada despues d q termina d cargar el logo d Ubuntu

despues d esto la instalacion sigue igual q concualkiera... ahora lo unico q keda por resolver es como hacer q la placa integrada Via ande como corresponde! pero bue... eso es otra cosa!



desde ya muchas gracias a todos los q me ayudaron la noche del sabado a intentar instalar 8.10, no c como no nos dimos cuenta antes :P pero bue... sirvio para darme cuenta d q cuando no es tan facil, es mas grande la alegria q uno tiene cuando lo logra! :KS


Cualkier duda me mandan mensaje y les doy mas informacion sobre como hice... pero creo q con esa van a poder instalar trankilamente cualkier version d 8.10 u 9.04....

---

### Post by josecuervo86 on 2009-04-27
Felicidades capo!

---

### Post by z37a on 2009-04-27
Que groso, encontraste el error, bien ahí!!!!

---

### Post by guillermolisi on 2009-04-27
Si hay hardware complicado para Ubuntu es VIA. De hecho pido cualquier chipset, bah en realidad me gusta muchisimo nForce, pero que no sea VIA.

---

### Post by zeroadrenaline on 2009-04-27
Felicitaciones. Como costó instalar eso!.

---

### Post by LuisTuc on 2009-04-27
La Verdad Costo mucho... pero bue... y si.. Como dice Guillermo me esta dando un dolor d Cabeza muy Grande la Placa VIA... estan todos los driver super actualizados y aun asi no puedo hacer andar al 100%... ya encontrare la manera y la colgare en el foro tambien!!

---

### Post by z37a on 2009-04-28
> **guillermolisi said:**
> Si hay hardware complicado para Ubuntu es VIA. De hecho pido cualquier chipset, bah en realidad me gusta muchisimo nForce, pero que no sea VIA.

Yo prefiero intel, la mala suerte es que em gustan los micros AMD!!!

Con VIA también tuve hace poco alguna experiencia con una placa de video y no logre activarle el 3d nunca.

---

### Post by faktorqm on 2009-04-28
Instalate 9.04 antes de que sea demasiado tarde (?)

---

### Post by letiun on 2010-11-15
buenas! alguna solucion para instalar ubuntu 10.10??

---

### Post by guillermolisi on 2010-11-15
> **letiun said:**
> buenas! alguna solucion para instalar ubuntu 10.10??

Podrias explayarte un poco mas en tu necesidad porque asi, tan sintetico, no se entiende bien cual es tu situacion y tampoco si esta relacionado con el asunto del thread.

---

