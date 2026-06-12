---
title: "Espacio Mínimo"
date: 2010-11-21
forum: Hardware
---

### Post by Domino476 on 2010-11-21
Hola, les escribo mi duda, tengo una Pc, q me regalaron , ya con sus años y un poco actualizada, pero tiene un disco muy pequeño (20GB) mi intensión era instalar Xubuntu 10.10, pero sin perder el SO instalado (aunq no lo quiera hay veces q todavía lo necesito), entonces llendo al grano mi pregunta era q espacio mínimo le debo dedicar al Xubuntu, incluido el SWAP. Muchas Gracias. Saludos

---

### Post by marcelo_bur on 2010-11-21
Hola. Ante todo y para ganar tiempo... ¿Qué OS tenes instalado y cuanto espacio libre queda en tu HD? Decis que la PC tiene sus años, así que también sería interesante conocer los datos del procesador y de cuanta RAM dispone ya que puede ocurrir que no tenga la capacidad necesaria para correr bien Xubuntu 10.10
Saludos

---

### Post by Domino476 on 2010-11-21
Gracias por responder; ahora no tengo muy presentes los datos; pero es un win xp de aprox 4GB; la memoria es de 512 MB; y el procesador no recuerdo....
Saludos

---

### Post by Domino476 on 2010-11-22
Especifico datos: Win Xp; AMD Duron 891 MHz; Memoria 512 MB; Placa de video 32MB; Lecto grabadora de CD; Disco 19 GB (16.2 libres).
Agradezco quien me brinde informacion. Saludos;)

---

### Post by guillermolisi on 2010-11-23
Si los Duron son equivalentes a los Pentium III no va a funcionar con 10.10 porque el kernel Linux utilizado a partir de esa version soporta desde Pentium IV o mayor.

Probaria con 10.04 pero dejando el XP en el disco estara bastante comprometido el espacio disponible. Se puede pero hay que tener bien en claro como particionar para Ubuntu de modo de aprovechar al maximo lo que queda del disco (que estara sujeto a para que usaras esa maquina).

---

### Post by alfplayer on 2010-11-23
Se podría hacer una swap de 1 GB y el resto una partición para root.

> **guillermolisi said:**
> Si los Duron son equivalentes a los Pentium III no va a funcionar con 10.10 porque el kernel Linux utilizado a partir de esa version soporta desde Pentium IV o mayor.

En realidad, 10.10 se puede instalar en Pentium III, como había explicado en [*este comentario*]("http://ubuntuforums.org/showpost.php?p=10064094&postcount=21"). Por lo que encontré en [*esta página*]("http://www.sourcemage.org/HardwareDetectionProcessors"), el Duron tiene *cmov*, por lo que también podría instalarse en un Duron.

---

### Post by guillermolisi on 2010-11-23
> **alfplayer said:**
> Se podría hacer una swap de 1 GB y el resto una partición para root.



En realidad, 10.10 se puede instalar en Pentium III, como había explicado en [*este comentario*]("http://ubuntuforums.org/showpost.php?p=10064094&postcount=21"). Por lo que encontré en [*esta página*]("http://www.sourcemage.org/HardwareDetectionProcessors"), el Duron tiene *cmov*, por lo que también podría instalarse en un Duron.
El condicional que estas usando deja ver que a pesar de la info citada te queda alguna duda. :)

La mia es: La gente de desarrollo del kernel dijo que a partir del 2.6.35 el kernel no soporta otros procesadores inferiores a PIV para reducir su tamaño. De hecho hay un caso en este subforo en el que el usuario no logro hacer funcionar 10.10 con una procesador que posee cmov, por lo cual esto me hace pensar que no es solo tener o no tener cmov para que funcione.

---

### Post by alfplayer on 2010-11-23
> **guillermolisi said:**
> El condicional que estas usando deja ver que a pesar de la info citada te queda alguna duda. :)

La mia es: La gente de desarrollo del kernel dijo que a partir del 2.6.35 el kernel no soporta otros procesadores inferiores a PIV para reducir su tamaño. De hecho hay un caso en este subforo en el que el usuario no logro hacer funcionar 10.10 con una procesador que posee cmov, por lo cual esto me hace pensar que no es solo tener o no tener cmov para que funcione.

Estuve buscando más información de esta cuestión de compatibilidad. En el hilo de mi comentario, el que tiene el error de cmov (marcelo_bur, que no es el que creó el hilo) sería con un K6-2, que es i586 sin cmov. Hay varios en la web que reportan instalar sin problema 10.10 en Pentium III. En las *release notes* de 10.10 solo se informa que los pre-i686 y los i686 sin cmov no funcionan más.

---

### Post by Domino476 on 2010-12-03
Perdón por la tardanza, pero gracias por interesarse en mi tema. Aclaro un par de cosas mas, para ver si me pueden ayudar mejor...
Mi interés, ademas de si funciona, yo creía q no iba a haber problemas, es el espacio mínimo q necesito (para swap y para el resto) para decidir entonces si realizo o no la instalación.

Si la versión live CD del XUBUNTU, me anduvo, significa q no voy a tener problemas de compatibilidad del procesador, para dicho sistema?

Gracias nuevamente, agradezco mayor información.
Saludos

---

### Post by alfplayer on 2010-12-04
No hay un límite fijo. Con 5 GB se podría instalar, pero lo mejor sería dedicarle la mayor cantidad posible de espacio. Hay que pensar que ni se podría bajar un DVD. Por lo menos, recomiendo 10 GB, así con suerte puede durar uno o dos meses :)

Xubuntu no es muy liviana. Lubuntu es más recomendable en mi opinión para esa computadora.

El procesador no debe causar un problema.

---

