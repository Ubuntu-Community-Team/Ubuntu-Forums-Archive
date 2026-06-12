---
title: "Dos Audios diferentes en los auricualres y los speakers"
date: 2011-11-29
forum: Hardware
---

### Post by c4d0rn4 on 2011-11-29
Hola gente!!

[SIZE="1"]Yo de nuevo por acá, ya ni se acordaran, pero bueno de una pc tirste ahora tengo algo decente. Por motivos varios, volví a linux y siempre es un gusto y un disgusto... pero bue, así son los amores! jajaj xD[/SIZE]

Lo busco es eso: Dos Audios diferentes en los auriculares y los speakers; con los drivers realtek en W7 andaban como digo, 

[[IMG]http://i.minus.com/jb1MzMKteWpGow.png[/IMG]](http://min.us/lb1MzMKteWpGow)
Parece que no me reconoce los headphones? Actualmente los headphones y los speakers al mismo tiempo reproducen el mismo audio. Tampoco puedo manejar el volumen por separado.

La verdad no se por donde buscar =S

Intenté con esto:
[http://ubuntuforums.org/showthread.php?t=878608](http://ubuntuforums.org/showthread.php?t=878608)
Instalar los drivers de realteak, pero lo unico que conseguí es que no me reconociera NADA y quedarme sin sonido.

Afortunadamente, a fuerza de synaptic y esta guía [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) quedó todo tal cual como arranqué.

Por si no se entiende lo que quiero hacer, me explayo un poco más. En los headphones tenía el audio principal (chrome-youtube) y en el otra habitación, hay un equipo de musica que toma el otro audio (un playlist en vlc).

---

### Post by alfplayer on 2011-11-30
Lo único que habría que hacer es elegir la salida de las aplicaciones con pavucontrol. No habría necesidad de instalar drivers porque ese dispositivo de audio ya está soportado por GNU/Linux.

---

### Post by c4d0rn4 on 2011-11-30
Si y no.

El tema es que me reconoce el audio digital, pero no me reconoce por separado los headphones y los speakers, me los toma como una sola salida analógica y tengo duplicado el audio. El digital no lo uso por que el hometheater no tiene entrada hdmi, así que directamente lo uso con la salida analógica del speaker en win.

---

### Post by alfplayer on 2011-11-30
Con pavucontrol qué salidas aparecen? Con PulseAudio el audio se administra principalmente con pavucontrol, que es más importante que alsamixer.

---

