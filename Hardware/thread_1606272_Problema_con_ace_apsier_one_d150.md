---
title: "Problema con ace apsier one d150"
date: 2010-10-26
forum: Hardware
---

### Post by sitodonosti on 2010-10-26
Hola, una amiga me ha pedido que le instalara ubuntu en su acer AspireOne 150d, el caso es que me he decidido a instalarle ubuntu netbook remix.
El problema es que lo he instalado y a los 2 minutos se bloquea el ordenador no funciona ni el teclado ni raton, pero si le doy al boton de apagar me aparece la pantalla que da opciones de apagar, reiniciar, etc.

He probado tambien con ubuntu 10.10 y me pasa lo mismo.

Sabeis que puede ser? no creo que sea por los requisitos....

---

### Post by Applelnx on 2010-10-26
Como funcionaba desde el LiveCD?
Te reconocia todo?
En la instalacion, le pusiste que te instalara los drivers privativos?

---

### Post by sitodonosti on 2010-10-27
> **Applelnx said:**
> Como funcionaba desde el LiveCD?
Te reconocia todo?
En la instalacion, le pusiste que te instalara los drivers privativos?

Utilice usb, pero si por liveCD, la imagen es la misma
pues no lo probé le di a instalar pero en principio si que me lo tenia que reconocer porque va durante dos minutos y después ná!
mmm creo que si le dije que me los pusiera, puede ser eso?
Pero esque lo que más me extraña es que durante cierto tiempo vaya y después deje de funcionar...

---

### Post by Applelnx on 2010-10-27
Se me ocurre que puede ser por eso. Yo haria la prueba de correr Ubuntu Remix desde el USB un largo rato, a ver si te pasa lo mismo. 

Mientras estas ahi, podrías fijarte en el /var/log/syslog (del disco donde esta instalado) con la fecha y hora cuando dejo de funcionar, y postear aca las ultimas lineas antes de que se cuelgue el sistema. Con eso supongo que podemos tener una idea mas precisa de la causa del error.

Saludos

---

### Post by sitodonosti on 2010-10-30
> **Applelnx said:**
> Se me ocurre que puede ser por eso. Yo haria la prueba de correr Ubuntu Remix desde el USB un largo rato, a ver si te pasa lo mismo. 

Mientras estas ahi, podrías fijarte en el /var/log/syslog (del disco donde esta instalado) con la fecha y hora cuando dejo de funcionar, y postear aca las ultimas lineas antes de que se cuelgue el sistema. Con eso supongo que podemos tener una idea mas precisa de la causa del error.

Saludos

ok, he estoy instalando ahora mismo ubuntu 10.10 no el notebook remix, asique supongo que si ubuntu con gnome funciona el ubuntu remix deberia de funcionar.

El syslog, creo que esta con ubuntu también y no con el remix.

---

### Post by sitodonosti on 2010-11-04
Vale ya lo he instalado y tal, lo único que ahora me falla es que me pongo a descargar idiomas y se bloquea tarda muxiiisimo. Y además el touchpad no funciona, probe en poner un raton por usb y si que funcionaba.

Alguna idea¿?
gracias!

---

### Post by Applelnx on 2010-11-06
> **sitodonosti said:**
> Vale ya lo he instalado y tal, lo único que ahora me falla es que me pongo a descargar idiomas y se bloquea tarda muxiiisimo. Y además el touchpad no funciona, probe en poner un raton por usb y si que funcionaba.

Alguna idea¿?
gracias!

Lo de los idiomas puede ser por los repositorios. A mi los de Argentina me funcionaban muy lentos y cambie a unos de Brasil. Para cambiarlos, entras a Sistema - Administracion - Gestor de paquetes Synaptic y despues a Configuracion - Repositorios. Donde dice "Descargar desde" podes elegir otro repositorio.

En cuanto al touchpad, puede ser que no lo puedas activar? Nos podes dar mayor detalle del problema? Cuando lo probaste desde el livecd funcionaba?

Saludos

---

### Post by sitodonosti on 2010-11-07
> **Applelnx said:**
> Lo de los idiomas puede ser por los repositorios. A mi los de Argentina me funcionaban muy lentos y cambie a unos de Brasil. Para cambiarlos, entras a Sistema - Administracion - Gestor de paquetes Synaptic y despues a Configuracion - Repositorios. Donde dice "Descargar desde" podes elegir otro repositorio.

En cuanto al touchpad, puede ser que no lo puedas activar? Nos podes dar mayor detalle del problema? Cuando lo probaste desde el livecd funcionaba?

Saludos

Pues nose laverda pero se me bloquea cuando esta actualizando idiomas o cuando abro dos cosas es como si se saturara el ordenador y se realentizara.

lo de touchpad no funciona en liveCD asique me imagino que esa info la podré encontrar por internet para ver como activarlo, de momento me funcionaba con un muse por usb
El caso eseque e probado con netbook remix ubuntu 10.10 y ubuntu 10.04 y cunado le empezaba dar un poco de caña por asi decirlo se bloquea...

---

