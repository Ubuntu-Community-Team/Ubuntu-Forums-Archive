---
title: "placa wifi compatible"
date: 2011-03-01
forum: Hardware
---

### Post by mano negra on 2011-03-01
Buenas, 
  ando buscando una placa wifi para mi pc de escritorio. Estuve por comprar una       [SIZE=1][COLOR=Black]Tp-link Tl-wn851n, pero resulta que, por lo que vi, es medio complicado el tema driver o directamente no hay. Saben de algunas o donde busco. Estoy usando Ubuntu 9.10.
Saludos
[/COLOR][/SIZE]

---

### Post by biale on 2011-03-01
No es una placa, es un dongle usb (?). Recien lo probe con un Karmic Koala y con señal plena conecto bien. Chip Atheros. Si tuve que reiniciar una vez la compu.

El punto es que conecta con norma G y no con norma N. Para la N hay que esperar a Maverick

---

### Post by guillermolisi on 2011-03-01
Esperar a Maverick ? ... Biale, ponete al dia ! :D

Ese dongle deberia funcionar, tal como entendi de lo que quiso significar Biale, si usas 10.10

---

### Post by biale on 2011-03-01
Gracias por la intervencion porque no se entendió bien..

El dongle funcionó con 9.10, a las velocidades de la norma "G"

El mismo dongle conecta con norma N/ Mimo (300 Mbps) con el nucleo 2.6.35. Nucleo de Maverick o un backported para Lucid.

La computadora de marras es una Pentium a 2.4 Ghz, por eso todavía sigue con Karmic. Y funciona bien...

---

### Post by mano negra on 2011-03-01
Disculpen, pero no entiendo nada. Lo que pensaba poner es una placa que se pone en la ranura pci (si no me equivoco). Nada de usb. Me imagino que tiene que haber compatible con ubuntu pero no se cuales. O en todo caso, que sean fáciles de conseguir los driver.
Salud!

---

### Post by guillermolisi on 2011-03-01
Los drivers de placas PCI habitualmente standard de la industria, por ejemplo Atheros, Realtek, Intel, nVidia, etc., vienen incluidos en el kernel (nucleo) del sistema operativo.

Para algunos chips tal vez haga falta bajar e instalar un driver en particular, que se agrega como modulo (driver externo al kernel).

En realidad tu pregunta deberia estar orientada al chip de la placa y no a la marca/modelo (si bien estan relacionados es mucho mas rapida la conclusion sobre su adaptabilidad a un ambiente Linux).

Personalmente me gustan las placas con chip Atheros siempre que no sean modelos recientes (2009 o anteriores) porque he leido casos de chips del 2010 problematicos.

---

### Post by biale on 2011-03-01
¿Soporta la compu USB 2.0?  Con una placa PCI perderías señal, en parte por la ubicación mas baja de la antena y en parte por el apantallado propio del chasis. Sumado a un conjunto mas fragil.

USB y cable alargador (o base que vende TP-LINK) es lo que mas resultado me ha dado.

Son solo ideas, quizás alguien pueda aportar una experiencia distinta...

---

### Post by biale on 2011-03-01
Si, también depende de la versión del chipset. Leo en la caja "versión 2.2".

---

### Post by hectorivand on 2011-03-02
> **mano negra said:**
> Buenas, 
  ando buscando una placa wifi para mi pc de escritorio. Estuve por comprar una       [SIZE=1][COLOR=Black]Tp-link Tl-wn851n, pero resulta que, por lo que vi, es medio complicado el tema driver o directamente no hay. Saben de algunas o donde busco. Estoy usando Ubuntu 9.10.
Saludos
[/COLOR][/SIZE]

Hola, la placa que mencionas trae un chip Atheros, que siguiendo lo que dice Guillermo más arriba por ahí hay problemas.

La que te recomiendo es la Dlink DWA-525 que viene con un chip Ralink 3060 (no es lo mismo que realtek) y en Ubuntu andan de una y muy bien. Soporta N hasta 150mpbs.

Saludos
Nacho

---

### Post by guillermolisi on 2011-03-02
> **hectorivand said:**
> ....

La que te recomiendo es la Dlink DWA-525 que viene con un chip Ralink 3060 (no es lo mismo que realtek) y en Ubuntu andan de una y muy bien. Soporta N hasta 150mpbs.

Saludos
Nacho
Coincido con esa recomendacion.

---

### Post by mano negra on 2011-03-02
> 
La que te recomiendo es la Dlink DWA-525 que viene con un chip Ralink 3060 (no es lo mismo que realtek) y en Ubuntu andan de una y muy bien. Soporta N hasta 150mpbs.


Justo estaba viendo que esa placa anda. Cuando la tenga les preguntaré si hay que hacer alguna instalación o configuración.
Gracias
Saludos

---

### Post by hectorivand on 2011-03-02
> **mano negra said:**
> Justo estaba viendo que esa placa anda. Cuando la tenga les preguntaré si hay que hacer alguna instalación o configuración.
Gracias
Saludos

Olvídate, no tenes que hacer nada, instalala y disfrútala, los drivers ya están incluidos en el Kernel y andan de 10.

Cualquier duda consulta.

Saludos
Nacho

---

