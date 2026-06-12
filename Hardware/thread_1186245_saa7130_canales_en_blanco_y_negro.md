---
title: "saa7130 canales en blanco y negro"
date: 2009-06-13
forum: Hardware
---

### Post by mama21mama on 2009-06-13
Hola, la tengo andando hace bastante ya, con la radio fm, control no me gaste porque no lo uso. Pero... :( se ven todos los canales en blanco y negro menos 2 o tres; probe todas las normas. Alguien le pasa lo mismo que a mi?

---

### Post by fmsismo on 2009-06-13
La configuraste para que trabaja en pal-n?  Yo tuve el mismo problema cuando la configuré como pal o ntsc.

Estas seguro que esta bien configurado el módulo.  Tenes que ver que sintonizadora tenes.

---

### Post by mama21mama on 2009-06-13
Esta es mi placa tal como sale con un lspci

> 01:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)



Y esta es la _[config]("http://mamalibre.eshost.com.ar/?q=node/1#comment-105")_ que use en el modulo.

Realmente no se que pasa.

---

### Post by fmsismo on 2009-06-13
Que programa estas usando para ver (o intentar ver la tele).  El formato de emición acá el pal-nc.

Yo estoy usando tvtime.  Tenes que saber que sintonizadora tiene tu placa.

La mías es:

01:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

Tuve que configurar el módulo con la sintonizadora que tiene. Cree un archivo /etc/modprobe.d/saa7134 con

[INDENT]options saa7134 alsa=0 card=3 tuner=39 
install saa7134 /sbin/modprobe --ignore-install saa7134[/INDENT]

Fijate que en estos post hay información.

[http://ubuntuforums.org/showthread.php?t=908812](http://ubuntuforums.org/showthread.php?t=908812)
[http://ubuntuforums.org/showthread.php?t=304444](http://ubuntuforums.org/showthread.php?t=304444)

Este script lo hice yo para probar sintonizadoras.

[http://ubuntuforums.org/attachment.p...7&d=1209132896](http://ubuntuforums.org/attachment.p...7&d=1209132896)

Saludos

---

### Post by mama21mama on 2009-06-13
Ya probe todas las normas.. pal, pal-nc, ntsc etc y etc. todas las probe.

Solo veo la mayoria de los canales en blanco y negro.

Mi sintonizadora es TV Tuner Pro - Encore ENLTV-FM (chip saa7130).


Tu script esta dificil de allarlo. :(

PD: uso XawTV ya que puedo grabar con el lo que veo.

---

### Post by juancarlospaco on 2009-06-13
Proba TVTime.
Es culpa de Norma.

---

### Post by mama21mama on 2009-06-13
ya lo probe, y todas las normas.

---

### Post by pablo.s on 2009-06-13
A veces sucede que cuando
no hay buena señal de cable,
las imagenes aparecen con
mucha lluvia, distorsión e
incluso, cuando la señal es
muy débil, en blanco y negro.
Yo verificaria la intensidad
de la señal, que los cables
estén en buen estado, y sobre
todo, que la señal llegue
de forma "directa".

---

### Post by mama21mama on 2009-06-13
A si veo actualmente tv. tambien probe conectando una vhs, dvd, videofilmadora. para ver si era problema de señal.

[http://www.youtube.com/watch?v=vilaNS1K23E](http://www.youtube.com/watch?v=vilaNS1K23E)

---

### Post by pablo.s on 2009-06-13
Por lo que veo no es 
problema ni de norma
ni de señal.
Segui participando.

---

### Post by mama21mama on 2009-06-13
:popcorn: mmm vere que hago.
tal ves la lleve a un tecnico elecronico.
años atras en m$ win se veia barvaro, y al poco tiempo en m$ win empezo a verse en blanco y negro; creo que es un bug de la placa ya que no solo a mi me pasa.

e escuchado en el irc que a otro le pasa lo mismo, debe ser una tirada de placas que vieneron adrede con vencimientos :D :D de componentes; tal vez sabotaje. anda saber.

---

### Post by sdennie on 2009-06-15
Estas usando Intrepid o Jaunty?  La placa mia hizo lo mismo hasta el kernel 2.6.26 (y ahora esta roto en otra manera en 2.6.30) asi que es possible que nunca va a funcionar con Intrepid.  Fijate con un Jaunty LiveCD para ver si funciona con un kernel mas nuevo.

---

### Post by mama21mama on 2009-10-14
Estoy en jaunty y nada de nada.
Mande un mail a soporte técnico de encore argentina, esperare a ver que me dicen ellos.

---

### Post by Mauro22 on 2009-10-14
> **mama21mama said:**
> Estoy en jaunty y nada de nada.
Mande un mail a soporte técnico de encore argentina, esperare a ver que me dicen ellos.

Yo hace un año que estoy esperando una respuesta de ellos jej...


Otra cosa, te fijaste la sintonia "fina" o algo asi, porque a mi me pasaba que si se la bajaba se me veia blanco y negro...


EL tvtime esta con la configuracion de fabrica? proba cambiando a "Aire" en vez de "cable"...

---

### Post by mama21mama on 2009-10-14
Ya probé todo, es algo de la placa.

---

### Post by mama21mama on 2009-10-14
> Buenos das, 

Gracias por contactarnos. 

Para contactos posteriores referentes a esta situacin, por favor indique el nmero de referencia al contactar el Centro de Clientes Encore Electronics, Inc: CID- 3872147 

Comprendo que tienes problemas con el dispositivo ENLTV-FM3 debido a que visualizas los canales en blanco y negro. 

Para poder solucionar el inconveniente te recomiendo verificar la "Norma". En la pantalla de configuracin de la sintonizadota: 

1.    En "TV Tuner Standard" selecciona "PAL_N" 
2.    Dentro de "TV Channel", en la opcin de "Country or Region" selecciona "Argentina". 
3.    Dentro de "TV Channel", en la opcin de "TV Scan Type" selecciona "Cable" 

Por ultimo verifica que el cable coaxial este bien conectado a la placa sintonizadota. Este puede ser otro de los motivos del inconveniente. 

Gracias por haber contactado al Soporte Tcnico de Encore Electronics, Inc. Si tiene ms preguntas, no dude en contactarnos nuevamente. 

Damin 
Soporte Tcnico de Encore Electronics, Inc. 


From: [email]mama21mama2000@yahoo.com.ar[/email] 
Date: 14.10.2009 23:25 
To: [email]soporte.argentina@encore-usa.com[/email] 
Subject: ENLTV-FM en blanco y negro 

Hola, tengo un problema con esta placa, no solo yo si no muchos. 
La placa es ENLTV-FM3, se me ve la mayora de los canales en blanco y 
negro. :s 

el chip que usa es saa7130 

Quisiera saber si es una anomala de la placa o no?; tambin le por ah 
que se debe cambiar un jumper para resetearla, realmente no se cual es 
el problema ya que antes funcionaba muy bien. 

Saludos 

-- 


mama libre 
[http://mamalibre.eshost.com.ar](http://mamalibre.eshost.com.ar) 

--

Me respondieron el mail, pero me dicen mas de lo mismo :s

---

