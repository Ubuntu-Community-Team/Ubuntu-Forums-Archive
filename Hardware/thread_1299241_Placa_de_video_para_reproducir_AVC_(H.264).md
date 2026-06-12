---
title: "Placa de video para reproducir AVC (H.264)"
date: 2009-10-23
forum: Hardware
---

### Post by gahia on 2009-10-23
Hola, 

Quería consultarles si los drivers para NVIDIA/ATI (actualmente utilizo los que instala envyng) soportan las extensiones de las placas para reproducción de AVC (H.264). Y qué aplicaciones de reproducción pueden utilizar dichas extensiones (Mplayer? VLC?)

Tengo instalado Kubuntu 9.04 e instalaré el 9.10 seguramente. Mi idea es comprar una placa NVIDIA o ATI (da igual) barata que me aliviane el micro cuando reproduzco video, pricipalmente en 1080p. Así que si tienen alguna idea de qué recomendarme o alguien que haya vivido la misma experiencia agradecido también.

Gracias!

---

### Post by pablo.s on 2009-10-24
> **gahia said:**
> Quería consultarles si los drivers soportan las extensiones de las placas para reproducción de AVC (H.264). Y qué aplicaciones de reproducción pueden utilizar dichas extensiones (Mplayer? VLC?)

Las extensiones que hacen uso del
GPU para mostrar video HD se llaman
VDPAU (Video Decode and Presentation
API for Unix) en tarjetas NVidia.
Si te interesa probar este tema, lo que
debés hacer es [agregar este PPA]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa"), donde
hay paquetes preparados para sacar
provecho a esta tecnología. En este caso
utiliza Mplayer, pero si buscás hay otros
PPA que utilizan VLC con este soporte.

> **gahia said:**
>  Mi idea es comprar una placa NVIDIA o ATI (da igual) barata que me aliviane el micro cuando reproduzco video, pricipalmente en 1080p. Así que si tienen alguna idea de qué recomendarme o alguien que haya vivido la misma experiencia agradecido también.

Lo que yo te recomiendo es NVidia
para este tema. No tengo idea de las
extensiones de las ATI. A mi me
funciona todo muy bien. No obstante
yo reproduzco más 720p que 1080p,
aunque he probado y funciona con
1080p de la misma forma. Prefiero
ver 720p porque es una resolución que
se ve perfecto y las bajadas son un 
tercio más pequeñas.

---

