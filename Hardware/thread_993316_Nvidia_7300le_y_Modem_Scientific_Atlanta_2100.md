---
title: "Nvidia 7300le y Modem Scientific Atlanta 2100"
date: 2008-11-25
forum: Hardware
---

### Post by NickCis on 2008-11-25
Quiero instalar el ubuntu 8.10 (64bits, por mi procesador Amd Athlon 64) Y estube leyendo sobre la compatibilidad de mi hardware, encontre dos problemas, uno mi placa Nvidia Geforce Xfx 7300le y el Modem.
Bue primero la placa, cuando instale el ubuntu, que problemas voy a tener con la placa?, de donde y como instalo sus drivers para su correcto funcionamiento?. Lei algo de los drivers libres y los propietarios, d Nvidia, que es eso?.

Despues el modem, este modem, el Scientific Atlanta 2100, es el que te provee multicanal cuando contratas cablemodem. Ahora lo tengo conectado por usb. Busque los drivers para linux, pero no los encontre, existen?, o lo voy a tener que conectar por ethernet?. El problema, es que la placa de red de la pc la estoy usando para compartir carpetas y internet con otra pc, que tiene xubuntu y xp instalados.
Ademas, como hago para compartir la internet y carpetas entre estas pcs?.

Saludos y muchas gracias.

---

### Post by santiagoward2000 on 2008-11-25
> **NickCis said:**
> Quiero instalar el ubuntu 8.10 (64bits, por mi procesador Amd Athlon 64) Y estube leyendo sobre la compatibilidad de mi hardware, encontre dos problemas, uno mi placa Nvidia Geforce Xfx 7300le y el Modem.
Bue primero la placa, cuando instale el ubuntu, que problemas voy a tener con la placa?, de donde y como instalo sus drivers para su correcto funcionamiento?. Lei algo de los drivers libres y los propietarios, d Nvidia, que es eso?.

BIENVENIDO! :)
Con el tema de la placa, la 7300 no debe tener ningún problema. Los drivers libres son los que ya vienen instalados, que te dejan que la placa ande, pero todavía no tienen aceleración 3D. Los drivers propietarios son los oficiales de NVidia. Como están registrados por ellos, Ubuntu no los trae intalados, pero tiene una aplicación que los instala por vos. Lo abrís desde **Sistema > Administración > Drivers de Hardware** (o algo parecido, lo tengo en inglés). Ahí marcás qué drivers querés instalar y se bajan e instalan solos (obvio, tenés que tener la conexión de internet andando).
Suerte!

---

### Post by faktorqm on 2008-11-26
20 posts en uno.... para la proxima te pido por favor que crees un thread nuevo por cada problema que tengas, asi es imposible responder y el que viene atras y lee no entiende nada.... 

placa de video: hace lo que te dijo santiago (el driver libre es uno sin aceleracion 3d, sin posibilidad de clonacion (creo)) o sino te instalas el envy-ng (un instalador que te instala el driver de nvidia original con aceleracion 3D y todos los chiches ;)). 

cablemodem: ¿estas seguro que no te reconoce el modem? lei por ahi que el kernel lo soportaba! por que decis que necesitas drivers? te fijaste si tiene salida ethernet? si tiene te conviene enchufarlo por ahi y listo. Si queres te compras otra placa de red (salen 15 mangos o menos) y puenteas ahi para la otra pc o sino un switch pero ya es un poquito mas caro (alrededor de 50 mangos). Si te anda por usb listo el pollo.

guia de usuario del modem:[http://www.scientificatlanta.com/products/consumers/userguidepdfs/webstar_userguides/4017510.pdf](http://www.scientificatlanta.com/products/consumers/userguidepdfs/webstar_userguides/4017510.pdf)

para compartir internet: esto depende exclusivamente de que conexion al modem vayas a usar. Si usas usb a ethernet, ethernet a ethernet, etc. Primero decidi que vas a hacer y luego te ayudamos.

para compartir archivos: yo hice un hermoso tutorial para principiantes!! [http://ubuntu-ar.org/tutoriales/samba](http://ubuntu-ar.org/tutoriales/samba) y eso te explica absolutamente todo lo que queres saber. En teoria para tu ubuntu para con el xubuntu de la otra pc que tenes no te conviene usar samba, te conviene usar nfs, pero eso ya es algo mas avanzado. Como vos digas....

Salu2!! :KS

---

### Post by guillermolisi on 2008-11-26
> **NickCis said:**
> Despues el modem, este modem, el Scientific Atlanta 2100, es el que te provee multicanal cuando contratas cablemodem. Ahora lo tengo conectado por usb. Busque los drivers para linux, pero no los encontre, existen?, o lo voy a tener que conectar por ethernet?. El problema, es que la placa de red de la pc la estoy usando para compartir carpetas y internet con otra pc, que tiene xubuntu y xp instalados.
Ademas, como hago para compartir la internet y carpetas entre estas pcs?.

Saludos y muchas gracias.

Si ese cablemodem tiene salida USB y Ethernet, ni dudaria de usar la Ethernet.

Por que ?
Porque ganas en rendimiento y con Ubuntu sale funcionando sola la conexion a Internet via cablemodem.

Respecto de la segunda PC, tenes varias alternativas (como se comento en otro thread creo que en esta misma seccion del foro).

La mas economica es agregar una segunda placa de red, configurar NAT en la PC que posee la conexion a Internet y utilizar un cable cruzado para la segunda PC.

Luego tenes la misma solucion pero con la variante de incorporar un switch.

Ambas te obligan a dejar encendida la PC que posee la placa que te conecta con el cablemodem para que la segunda PC tenga acceso a ella.

Algo mas cara en terminos economicos es incorporar un router. Laburas menos (no tenes que configurar NAT ni agregar la segunda placa de red en la PC que conecta al cablemodem) pero invertis mas dinero.

---

### Post by NickCis on 2008-11-26
Bueno, me decidi por comprar la placa, tengo la otra pc conectada a esta por un cable de red cruzado.
Ahora instalo ubuntu, y veo como anda todo lo de la placa de video.
Por lo de compartir la internet, como hago?, tengo la otra pc conectada por un cable de red cruzado.

Saludos.

---

### Post by guillermolisi on 2008-11-27
> **NickCis said:**
> Bueno, me decidi por comprar la placa, tengo la otra pc conectada a esta por un cable de red cruzado.
Ahora instalo ubuntu, y veo como anda todo lo de la placa de video.
Por lo de compartir la internet, como hago?, tengo la otra pc conectada por un cable de red cruzado.

Saludos.

Te cuento como lo resolvi en mi casa (una desktop Ubuntu + un server Ubuntu + 2 PCs con Win).

En la maquina que tiene las dos placas de red, una a Fibertel y la otra a un switch (porque son mas de una maquina), instale Firestarter para poder configurar el firewall de Ubuntu y, de paso, habilitar las reglas para hacer NAT (Network Address Translation) y que las otras PCs salgan por el mismo enlace con la IP publica a Internet.
Use Firestarter para no lidiar directamente con las reglas en IPTables (o sea, Firestarter no es imprescindible pero si es comodo).

PC a Internet
eth0 con IP dinamica (la que otorga el cablemodem)
eth1 con IP fija (p.e. 192.168.0.10 255.255.255.0)

PC cliente
placa de red con IP fija (tomando el ejemplo de eth1 deberia ser p.e. 192.168.0.11 255.255.255.0, gateway 192.168.0.10, DNS 192.168.0.10)

Pregunta lo que necesites

---

