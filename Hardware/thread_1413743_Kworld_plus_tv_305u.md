---
title: "Kworld plus tv 305u"
date: 2010-02-22
forum: Hardware
---

### Post by themasterdark on 2010-02-22
Hola

Volvi de nuevo, bueno.

El problema es el siguiente esta capturadora de tv via usb, ya la tengo funcionando con tvtime y capturando el audio con sox (tambien se puede con arecord y aplay)

El problema es que el audio suena con bastante ruido y e probado bastantes ratios para caprutarlo, los comandos son

sox -s -c 2 -r 48000 -t alsa hw:1,0 -t alsa hw:0,0   (este es uno, el que funciona mejor)
 
sox -s -c 2 -r 44100 -t ossdp /dev/dsp1 -t alsa hw:0,0 (este es otro)

el problema es que forma que use para capturar el sonido suena con bastante ruido...
y no es gratos ver television asi.

Espero me den alguna mano =)

^^

Saludos

---

### Post by themasterdark on 2010-02-23
Y me vuelvo a responder jajajaj
aunque no logre realizarlo de la forma mas comoda para cualquiera.
lo logre sacando una calidad de audio mejor que el doble de la que tenia al menos eso creo. =)

por si alguien tiene la kworld plus tv 305u subire los pasos mañana porque ahora tengo sueño jaja.


Saludos a todos ;)

---

### Post by Carlos C on 2010-02-24
¿y bien, cómo es que lo solucionaste?

---

### Post by themasterdark on 2010-02-24
a sorry jajaja se me habia olvidado contestar...

primero que nada descargar e instalar este paquete... controlador del chip em28xx 

con el que viene esta capturadora y bastantes otras, en la pagina existen paquetes para 32 y 64 bits

[http://jiemeb.free.fr/pinnacle/](http://jiemeb.free.fr/pinnacle/)

Luego, crear un script dejare el que uso yo ya que es el que me dio mas resultados.

#!/bin/sh
pactl load-module module-loopback
sox -s -c 2 -r 48000 -t alsa hw:1,0 -t alsa hw:0,0 & tvtime -c 24 -M;
wait 1 tvtime
killall sox;
killall tvtime;
killall -9 pulseaudio;

En ese script interviene sox, que se instala asi:

sudo apt-get install sox

bueno se le da permiso de ejecucion al script

sudo chmod /usr/bin/nombre_del_script

y se ejecuta como se desee.. en una consola, presionando alt + f2, o agregandolo al menu.

listo =)

si ven que funciona raro el  sonido.. solo abren las preferencias de sonido de gnome (si estan en gnome xD)
la capturadora es detectada dos veces en el sonido 
- analog stereo input
- digital stereo input

y cambian de analog a digital o visceversa, lo mismo hacen si se pone feo el sonido al cambiar de canal =)


Eso espero le ayude a alguien ^^

o consulte =)

---

### Post by ojvulluz on 2010-03-16
buenisimo

yo estoy por comprar esa placa (si la consigo) asi que cualquier problema te consulto, pero está clarísimo.

una cosa nomas: tenes los assign de card y tuner apropiados para la Kworld?

Gracias!!!!

osvaldo.

---

### Post by themasterdark on 2010-03-16
por algun lado lei los tuner es cosa de buscar, pero despues de probar el modulo con el y sin el la calidad de imagen era la misma asi que no es necesario desde mi punto de vista, actualmente tengo funcionando la capturadora de tv, asi que consultas si llega a tus manos y tienes algun problema.

Saludos =)

---

### Post by ojvulluz on 2010-05-05
Funciona!!!

Gracias!!

Osvaldo.

---

### Post by themasterdark on 2010-05-06
Que bien que funcione, pero ¿te cuento algo?, en lucid funciona el sonido y video mucho mas fácil...

solo conectas la capturadora...

instalas el firmware...

instalas tvtime...

y listo jajaja xD

ya arreglaron el detalle del audio...

Saludos.!

---

### Post by whitecker on 2010-09-30
Me pueden dar una mano? No se en que fallo pero no me funciona.

1.- Instalo el firmware em28xx_32-24_i386.deb
2.- Instalo el tvtime y lo configuro como NTSC y Cable
3.- sudo geany /etc/tvtime/tvtime.xml y configuro video1 (esto es porque mi notebook toma la web cam como video0)

Luego cuando luego cuando ejecuto el TVTime se cuelga la aplicación. Para cerrarla de de la única forma que lo puedo hacer es con un xkill.

Lo mas extraño es que cuando reinicio la notebook me aparece un mensaje diciendo que el alsa esta colgado. Le doy aceptar para reiniciar igual y se cuelga mal el sistema operativo. Finalmente termino apagando la notebook apretando el boton de power.

Lo mas loco es que cuando la vuelvo a encender la notebook esta no funciona mas, no se carga el bios... De casualidad descrubri que sacando las memorias ram por un rato, al volver a poner las memorias ahí vuelve a encender la notebook y carga el sistema operativo normalmente.

Aunque parezca loco esto ya me paso varias veces cuando intento ver si funciona la tv con el tv time...

Tienen idea de porque me pasa esto? En que me estoy equivocando?

Les comento que mi notebook es una Toshiba A210-SP6811 con placa de video ATI X1250 y  no utiliza drivers privativos para la placa de video. Mi ubuntu es el 10.04


Bueno, si alguien me puede ayudar estaré mas que agradecido.

Saludos.-

---

### Post by themasterdark on 2010-10-01
Te recomiendo crees un thread nuevo con tu consulta, para no desordenar el foro.

Por otro lado es bastante extraño se te cuelgue el sistema a tal punto, parte por eliminar ese paquete que bajaste el que anteriormente recomendaba yo mismo (mis disculpas si fue eso).

e instala el siguiente paquete directamente de los repositorios 

sudo apt-get install linux-firmware-nonfree

ya que el contiene el firmware para esta capturadora usb.

luego verifica donde esta el dispositivo en video0 o video1, posterior a ello podrías reinstalar tvtime por cualquier problema que tuviese.

Luego configura todo y pruebas como te fue, pero te sigo recomendando habrás un nuevo thread

---

