---
title: "Notebook - Display no se apaga - Karmic"
date: 2009-11-01
forum: Hardware
---

### Post by sitiomatic on 2009-11-01
Hola.
Ayer instale Karmic y me pasa que cuando la notebook no esta en uso, el display no se apaga. Se pone negro, pero queda como el brillo encencido.
En jaunty se apagaba. Mire en el gestor de energia pero no le encuentro la vuelta.
Alguna idea?

---

### Post by moreback on 2009-11-01
Se supone que la opción que te apaga la pantalla es la que dice "Poner la pantalla en reposo si está inactivo durante:" dentro de las Preferencias del Gestor de energía. Ahí seleccionas la cantidad de minutos que quieras.

---

### Post by luks911 on 2009-11-01
> **sitiomatic said:**
> Hola.
Ayer instale Karmic y me pasa que cuando la notebook no esta en uso, el display no se apaga. Se pone negro, pero queda como el brillo encencido.
En jaunty se apagaba. Mire en el gestor de energia pero no le encuentro la vuelta.
Alguna idea?

Tengo el mismo problemita en uan Dell Inspiron 1545. Pero es aleatorio, a veces se apaga y a veces queda negra y encendida como decís. Además, en Jaunty se apagaba cuando bloqueaba la pantalla: primero se ponía negra y, en mi caso, a los 10 minutos, se apagaba. Ahora no. Sólo queda negra.

> **moreback said:**
> Se supone que la opción que te apaga la pantalla es la que dice "Poner la pantalla en reposo si está inactivo durante:" dentro de las Preferencias del Gestor de energía. Ahí seleccionas la cantidad de minutos que quieras.

Sí, eso lo revisé y está igual que en Jaunty. Y aun así el comportamiento es distinto.

Por otra parte, y aunque no creo que esté relacionado, me pasa en el SMplayer en pantalla completa que cada tanto aparece el cursor del mouse, cosa que antes no sucedía, y en el VLC la pantalla se pone negra cada 10 minutos si no muevo el cursor, incluso diciéndole al gestor de energía que no apague la pantalla.:roll:

---

### Post by rvm4000 on 2009-11-01
> **luks911 said:**
> Por otra parte, y aunque no creo que esté relacionado, me pasa en el SMplayer en pantalla completa que cada tanto aparece el cursor del mouse, cosa que antes no sucedía

Quizás sea por esto:
[A mouse pointer keeps reappearing during video playback in smplayer](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/455073). 
En realidad es un bug del mplayer de karmic.

---

### Post by luks911 on 2009-11-01
> **rvm4000 said:**
> Quizás sea por esto:
[A mouse pointer keeps reappearing during video playback in smplayer](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/455073). 
En realidad es un bug del mplayer de karmic.

Muchas gracias.
En realidad usaba el mplayer-nogui, aunque tengo tu repositorio. Ahora lo saqué para instalar el MPlayer que empaquetaste. Con eso debería quedar solucionado, después lo pruebo.
De nuevo gracias, por el dato y por el trabajo con SMplayer, que es genial.

---

### Post by josecuervo86 on 2009-11-01
No estara metido en el medio el protector de pantalla?

---

### Post by luks911 on 2009-11-01
El bug tiene que ver con eso, sí. Pero las opciones las tengo igual que en Jaunty y antes no pasaba.

---

### Post by sitiomatic on 2009-11-01
No se si sera esto, y si es, es muy tonto :)
Estaba activado el salvapantallas en una opcion que decia "oscurecer pantalla", al activarse el salvapantallas pone la pantalla negra, pero encendida (esta corriendo el salvapantallas)
Lo cambie por otra opcion y al andar el salvapantallas con imagenes tener la pantalla encendida me resulta obvio. A la media hora se apaga como dice el gestor de energia.
Sera asi?

---

### Post by josecuervo86 on 2009-11-01
> **sitiomatic said:**
> 
Sera asi?
99.9% seguro ;)

---

