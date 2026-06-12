---
title: "No tengo internet con Ubuntu"
date: 2009-07-01
forum: Hardware
---

### Post by BuIsPa on 2009-07-01
Hola que tal soy nuevo en esto de ubuntu, pero no voy tan mal es programa hace todo por mi no tube que instalar drivers ni nada ubuntu reconocio mi placa mader, micro, todo, solo q tengo un problema yo tengo internet inalambrico a traves de un pendrive inalambrico (Noganet), en mi cuarto por supuesto la pc servidor tiene conectado un modem Enconre, y un Router D.Link300 pero cuando estoy con win anda perdecto pero con ubuntu no pasa nada como que no lo reconoce, que puedo hacer alguna idea ?

---

### Post by staar on 2009-07-01
primero que nada, abrí una Terminal (Aplicaciones > Accesorios > Terminal), corré ```
lsusb
``` y pega la salida acá, para que podamos saber si el sistema reconoce el dongle wifi (creo que asi se llaman), y en ese caso que modelo exacto es, y si necesita algún driver o toque especial...

saludos

---

### Post by BuIsPa on 2009-07-01
> **staar said:**
> primero que nada, abrí una Terminal (Aplicaciones > Accesorios > Terminal), corré ```
lsusb
``` y pega la salida acá, para que podamos saber si el sistema reconoce el dongle wifi (creo que asi se llaman), y en ese caso que modelo exacto es, y si necesita algún driver o toque especial...

saludos

Bus 001 Device 003: ID 04cf:8819 Myson Century, Inc. 
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Adaptador Inalambrica Marca: Noganet Modelo: KN-W520U
Espero que exista algun " Toque especial " por que driver no hay, para linux, si para win . !

---

### Post by jpoeta on 2009-07-02
Ubuntu es especial y no solo especial si no espacial!
Solo se trata un poco de configurar. :guitar:

Te dejo 2 Interesantes links el Primero en español y el segundo en inglés
espero te ayude =) 

Aquí no hay toques

Ubuntu es una comunidad, una forma de vida =) 

[Instalación de Wifi]("http://www.taringa.net/posts/linux/2635906/Linux-Wireless---Drivers-nativos-Wi-Fi-en-Linux_.html")

[Proyecto Linux Wireless en Inglés]("http://wireless.kernel.org/")

Saludos

Jpoeta;)

---

### Post by BuIsPa on 2009-07-02
> **jpoeta said:**
> Ubuntu es especial y no solo especial si no espacial!
Solo se trata un poco de configurar. :guitar:

Te dejo 2 Interesantes links el Primero en español y el segundo en inglés
espero te ayude =) 

Aquí no hay toques

Ubuntu es una comunidad, una forma de vida =) 

[Instalación de Wifi]("http://www.taringa.net/posts/linux/2635906/Linux-Wireless---Drivers-nativos-Wi-Fi-en-Linux_.html")

[Proyecto Linux Wireless en Inglés]("http://wireless.kernel.org/")

Saludos

Jpoeta;)

Hola, la verdad, lei el post de taringa yy bueno q te puedo decir no me ayudo en nada ya q no encontre el dispositivo q yo uso en el cuadro que alli postearon, el otro post traduco por google no ayudo en nada ya que no dice nada acerca del problema q tengo yo, bueno espero que haya otra solucion ...

---

### Post by staar on 2009-07-02
el autor de ese post en taradinga tiene el mismo adaptador que vos, lo importante es el chip, en este caso un Realtek RTL8187, igual ese tuto es algo avanzado para alguien que recién empieza...

en teoría, ese adaptador esta soportado out-of-the-box por ubuntu, cuando lo conectás, te figura para conectarte a una red inalámbrica en el applet de red, al lado del reloj?

saludos

---

### Post by alfplayer on 2009-07-02
Yo tengo también RTL8187, funciona con Ubuntu 8.10 y 9.04.

En mi experiencia lo único que hay que hacer es configurarlo haciendo click en el ícono en el panel de Ubuntu con los dos monitores (para configurar la red), y ahi elegir la red que se quiere usar que puede ser la de casa o la de una oficina. Por un bug ahi aparecen las redes con niveles de señales mucho más bajos de lo que son en realidad (al tener la computadora al lado del router esto para mi no es un problema).

Importante: puede parecer que no está siendo detectado porque cliqueando con el botón derecho en ese ícono no hay rastros del adaptador usb wifi.

---

### Post by BuIsPa on 2009-07-03
> **alfplayer said:**
> Yo tengo también RTL8187, funciona con Ubuntu 8.10 y 9.04.

En mi experiencia lo único que hay que hacer es configurarlo haciendo click en el ícono en el panel de Ubuntu con los dos monitores (para configurar la red), y ahi elegir la red que se quiere usar que puede ser la de casa o la de una oficina. Por un bug ahi aparecen las redes con niveles de señales mucho más bajos de lo que son en realidad (al tener la computadora al lado del router esto para mi no es un problema).

Importante: puede parecer que no está siendo detectado porque cliqueando con el botón derecho en ese ícono no hay rastros del adaptador usb wifi.


Nunca tube internet con ubuntu hasta ayer !, nose que paso pero pude entrar a paginas abir msn y demas, pero paso algo muy raro. En Xp el adaptador inalambrico tiene una luz q brilla cuando ay transferencia de datos, por ende esta titilando la luz todo el tiempo eso era normal para mi, pero de repente tube señal en ubuntu, nadie sabe por que, sin que  instale nada, y la luz del apaptador estaba Completamente apagada, como si no habria transferencia de datos, es muy raro, desp no se por que reinicie y se termino lo q se daba no tube mas señal.........--------> Alguien me ayuda a instalar ese driver del que hablan arriba ???

---

### Post by alfplayer on 2009-07-03
Seguro que no funcionó "por arte de magia". Tratá de hacer lo mismo que hiciste para qué funcione de nuevo, y contanos si siempre te quedás sin internet después de reiniciar Ubuntu. La luz no creo que sea un problema grave. Si funciona el driver que está, no encuentro necesidad de probar otro.

---

### Post by BuIsPa on 2009-07-06
> **alfplayer said:**
> Seguro que no funcionó "por arte de magia". Tratá de hacer lo mismo que hiciste para qué funcione de nuevo, y contanos si siempre te quedás sin internet después de reiniciar Ubuntu. La luz no creo que sea un problema grave. Si funciona el driver que está, no encuentro necesidad de probar otro.

No hice nada para que funciono, funciono solo jajaj te juro que no hice nada, pero desp de q reincie nose conecto mas, o sea la reconoce a la red pero dice que no se puede concectar, solo me conecte una sola vez y se ve q esa vez andaba bien por que empezo a actualizarce y a descargar cosas a una velocidad q con xp nunca habia llegado, la verdad q es genial ubuntu el poco tiepo que me ando con internet fue genial, alguien q me ayude a solucionar esto por favor..

---

### Post by alfplayer on 2009-07-06
Qué pasa cuando hacés lo que yo hize (lo que puse en el mensaje 7)? Aparecen las redes para conectarse?

---

### Post by BuIsPa on 2009-07-06
> **alfplayer said:**
> Qué pasa cuando hacés lo que yo hize (lo que puse en el mensaje 7)? Aparecen las redes para conectarse?

Si si me aparecen las redes que ve, pero no se conectan, es verdad q tamb se ve la red con mucha mas baja señal de lo habitual, nose por que, tendre q instalar algo ?

---

