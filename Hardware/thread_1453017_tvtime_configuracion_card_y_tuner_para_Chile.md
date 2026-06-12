---
title: "tvtime configuracion card y tuner para Chile"
date: 2010-04-12
forum: Hardware
---

### Post by patrixter on 2010-04-12
[B]Hola Amigos de Ubuntu.cl me dirijo a uds para preguntar si en sus conocimientos alguien sabra configurar bien la tarjeta de tv Asus p 7131 (saa7134) para chile ya que por foro que busco no encuentro los datos precisos de card y tuner para escuchar el audio ya que solo tengo imagen .

de antemano Gracias

Patricio[/B]

---

### Post by xtremox on 2010-05-04
yo tengo esa misma para el audio tienes que ver el mixer de alsa y activar la linea de entrada algo asi

---

### Post by Patriciologico on 2010-07-15
Hola de acuerdo al [blog de kenmaster]("http://kubuntu-chile.blogspot.com/2006/06/tip-instalar-targeta-de-tv-pctronix.html") los parametros son ```
sudo modprobe -v saa7134 tuner=43 card=42
```

A mi me funciona, pero la radio y el control remoto no los he hecho funcionar,

Saludos

---

### Post by patrixter on 2010-12-23
CITA(patrizio @ Dec 20 2010, 01:36 PM) [[IMG]http://www.ubuntu.cl/vb/style_images/1/post_snapback.gif[/IMG]]("http://www.ubuntu.cl/vb/index.php?act=findpost&pid=13854")
[B][b]Amigos  de Ubuntu.cl me podrian ayudar con un problema que muchos han tenido y  es poder tener sonido en tvtime  ya que todavia no puedo  ver la tele  con audio. Primero contare que tengo una capturadora Asus my cinema  p7131 analoga en mi sistema Lucid Linx 10.4 Lts ,he probado todas las  soluciones que hay en san google a veces tengo sonido por algun script  que encuentro pero al rato se me va el audio de tvtime quiero decir que  los canales se ven nitidos la capturadora los configuro solo pero el  audio nada. HE PROBADO:

 pactl load-module module-loopback 


tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

Quiero decirles que la capturadora bajo Windows funciona perfectamente 
y quiero lo mismo en Ubuntu y tvtime que es uno de los mejores para ver tv en Linux.

Si tuvieran los parametros de  card y tuner de esa tarjeta para Chile se los agradeceria 

De antemano gracias

Patricio[/B][/b]


[B]SOLUCIONADO

de tanto buscar en foros linux y ubuntu logre dar con la solucion del audio en tvtime
primero edite archivo confuguracion tvtime   tvtime.xml  ( cambiar por mix )

 <option name="MixerDevice" value="/dev/mixer:mix"/> 

y luego instalar  kmix

abrir kmix y subir volumen

voila tvtime con sonido.[/B]

Espero esata solucion le sirva a muchos

Saludos 

Patricio

---

### Post by MarianoC on 2011-02-28
Buenas, yo estoy por comprarme esta sintonizadora...Pudieron hacer andar el control remoto sin problemas?? Gracias!!

---

