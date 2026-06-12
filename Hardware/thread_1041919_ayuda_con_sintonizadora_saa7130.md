---
title: "ayuda con sintonizadora saa7130"
date: 2009-01-17
forum: Hardware
---

### Post by fantasma-- on 2009-01-17
Se instalo sola cuando instale el ubuntu (Si tengo winxp) instale el tvtime y me toma todos los canales y se ve joya pero no tengo sonido. es una TV.AV capture de ST Labs con sus años. les pego lo que dice el lspci:
02:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
Si alguno tiene una idea se lo agradezco.

PD: No se si tiene algo que ver pero en dispositivos de audio tengo ademas de mi placa (SB live alsamixer) otra as que dice SAA7134 alsamixer, no se si es normal o si es lo que esta jodiendo.

---

### Post by staar on 2009-01-17
> PD: No se si tiene algo que ver pero en dispositivos de audio tengo ademas de mi placa (SB live alsamixer) otra as que dice SAA7134 alsamixer, no se si es normal o si es lo que esta jodiendo.

proba poniendo para que salga el sonido por esa otra placa...

sino, fijate en el control de volumen de ubuntu, que por ahi tenes algo en mute (probablemente el Aux)...

saludos

---

### Post by fantasma-- on 2009-01-17
en esa saa7134 alsa mixer puse todo en alto y en la sb también no esta nada muteado y tengo sonido en otras aplicaciones me parece que es la sinto la que no esta largando sonido. en win funca todo.

saludos matias

---

### Post by fantasma-- on 2009-01-18
a alguno se le cae otra idea?

---

### Post by atari130xe on 2009-01-19
Hola, yo tengo la misma placa, es la TV View una baratonga que me vino de regalo cuando compre los componentes de la PC, yo en Ubuntu no probé hacerla funcionar, (no tengo internet en casa y no puedo bajar los paquetes). pero en la cuestión de sonido fijate que la placa de TV en sí mismo no va a emitir sonido alguno, sinó que usa la placa que tengas instalada en el sistema, si te fijás la placa tiene una salida "audio out", y debe haberte venido con un cablecito negro con conector RCA común, ese cablecito vá en en Audio out de la placa de TV y se conecta a Audio in de la placa de audio que tengas en tu pc, o en aux, recién ahi vas a poder escuchar bien., Espero te haya servido de algo el comentario.
saludos y suerte!

---

### Post by fmsismo on 2009-01-19
Tiene tu placa una salida de audio (un miniplug)?

Yo tengo andando una saa7130 pero con el cable loopback.

Sale de la sintonizadora y entra en el linein de la placa onboard de mi equipo.

Probaste de enchufar parlantes a la salida de audio de la placa sintonizadora (si tenes la salida)?

Estas usando norma pal-nc (supongo que estas en argentina)?

Saludos

---

### Post by fantasma-- on 2009-01-19
si tiene el cable  a la placa de sonido y esta enchufado. el problema es que no sale audio de la sintonizadora(le puse los parlantes directos). estoy en pal-nc y el vídeo se ve joya el problema es el audio. También tengo el control de line in y por las dudas el de aux al taco. Lo que no se es por que me tira que tengo otra placa con el saa7130 (que es el chip de la sinto).
Saludos Matias

---

### Post by aljama on 2009-01-19
por lo que lei mas arriba, tienes dos placas de sonido, si es asi, tienes que conectar la salida de audio de la placa de tv a la entrada de linea o microfono de la placa de sonido que estas usando (onboard , pci, externa).
en el control de volumen te deja seleccionar las diferentes placas de sonidos, y revisar si estan activadas

---

### Post by fantasma-- on 2009-01-21
eso ya lo hice pero sigue sin tirar sonido la sintonizadora

---

### Post by fantasma-- on 2009-01-23
La verdad que bronca que no lo pueda sacar andando en Linux. les juro que el video se ve mejor que en win2 con los drivers originales de la placa. y a alguno le queda una sugerencia lo escucho.

---

