---
title: "¿Cuál placa de video puedo instalar?"
date: 2010-12-22
forum: Hardware
---

### Post by Hadso on 2010-12-22
Hola a tod@s. 
Tengo una PC bastante vieja, pero gracias a Ubuntu, anda muy bien. 
Hace ya más de un par de años que lo uso. 

El problema es que tengo una placa de video que no es compatible con este SO. 
A lo largo del tiempo, la compatibilidad ha ido mejorando (o es menos peor). Sucede que ahora, esta PC que utilizo en mi casa, la usaré para trabajar y ahí la cosa cambia. Si bien haré trabajo de oficina con ella, no creo poder soportar ocho horas diarias frente a un monitor que muestra como tironean los gráficos. 

Es por esto, que me gustaría instalar una placa de video que sea compatible con el SO. 
No entiendo nada de hard. 

¿Cuál placa me conviene instalar? ¿Cuáles son los precios? ¿Me sugieren algún comercio? (Estoy en Buenos Aires :P) 
Mi motherboard es: Asus K8V-MX VIA K8M800 Chipset. 

Desde ya muchas gracias!
Saludos,

---

### Post by gmunioz on 2010-12-22
Para esa mother es necesaria una placa AGP, en estos momentos
es posible conseguir por unos $280, la Nvidia Geforce 6200 512 Mb Agp 4x/8x o por unos $200 la de 256 Mb

---

### Post by Hadso on 2010-12-22
> **gmunioz said:**
> Para esa mother es necesaria una placa AGP, en estos momentos
es posible conseguir por unos $280, la Nvidia Geforce 6200 512 Mb Agp 4x/8x o por unos $200 la de 256 Mb

Gabriel. Muchas gracias por el dato. 
Luego de dejar el mensaje en el foro, consulté a un técnico cerca de mi casa. 
Me cobra $400 por adquirirla he instalarla, pero no la configura para Ubuntu. 
Entiendo que la compatibilidad de estas placas es muy buena con GNU/Linux en general.
Creo que no lo dije antes, pero mi idea es instalar Debian, para poder correr un soft de gestión para mi trabajo. 
Estimo que la NVIDIA que me sugeris irá bien con el mismo, y si no, no tengo otra opción. :P

¿Me sugeris algún lugar en particular para ir a comprarla?
El precio que me pasas es casi la mitad de lo que me pidieron en otro lado. 
Muchas gracias por tu tiempo. 
Saludos,

---

### Post by gmunioz on 2010-12-22
Hola:

Una búsqueda en Mercado Libre da esto:

[http://listado.mercadolibre.com.ar/Nvidia-Geforce-6200-512-Mb](http://listado.mercadolibre.com.ar/Nvidia-Geforce-6200-512-Mb)


Poner la placa es sencillo, abris el ordenador, sacas la chapita
del slot agp, tenes uno solo, y enhufas la placa. al iniciar pulsas del para entrar a la bios, deshabilitas la onboard, conectas el monitor a la nvidia y ya esta.
Te sugiero lleves el equipo al vendedor para que la instale el, para evitar problemas de
garantia.

En debian los driver se instalan a mano, sin grandes dificultades, lo único que ocurre es que con cada actualización del kernel (no son muy frecuentes)hay que reinstalarlos

su
apt-get install module-assistant build-essentials
m-a build nvidia
m-a install nvidia
dpkg-reconfigure xserver-xorg **(seleccionas nvidia)**

En la actualizacion del kernel solo hace falta

m-a build nvidia
m-a install nvidia

---

### Post by Hadso on 2010-12-22
> **gmunioz said:**
> Hola:

Una búsqueda en Mercado Libre da esto:

[http://listado.mercadolibre.com.ar/Nvidia-Geforce-6200-512-Mb](http://listado.mercadolibre.com.ar/Nvidia-Geforce-6200-512-Mb)

Poner la placa es sencillo, abris el ordenador, sacas la chapita
del slot agp, tenes uno solo, y enhufas la placa. al iniciar pulsas del para entrar a la bios, deshabilitas la onboard, conectas el monitor a la nvidia y ya esta.

En debian los driver se instalan a mano, sin grades dificultades, lo único que ocurre es que con cada actualización del kernel (no son muy frecuentes)hay que reinstalarlos

su
apt-get install module-assistant build-essentials
m-a build nvidia
m-a install nvidia
dpkg-reconfigure xserver-xorg **(seleccionas nvidia)**

En la actualizacion del kernel solo hace falta

m-a build nvidia
m-a install nvidia

Muchas gracias por tu respuesta. 
Creo que me animaré a instalar esa placa de video. 
Estimo que con ella ya no tendré problemas en lo gráficos. Los mismos se verán fluidos y no habrá tirones, verdad?
El uso que le daré a la PC, principalmente, será para oficina, sin perjuicio del algún juego que cargaré :D.
Muchas gracias por tu tiempo. 
Felices Fiestas.

---

### Post by Hadso on 2011-03-20
> **gmunioz said:**
> Hola:

Una búsqueda en Mercado Libre da esto:

[http://listado.mercadolibre.com.ar/Nvidia-Geforce-6200-512-Mb](http://listado.mercadolibre.com.ar/Nvidia-Geforce-6200-512-Mb)


Poner la placa es sencillo, abris el ordenador, sacas la chapita
del slot agp, tenes uno solo, y enhufas la placa. al iniciar pulsas del para entrar a la bios, deshabilitas la onboard, conectas el monitor a la nvidia y ya esta.
Te sugiero lleves el equipo al vendedor para que la instale el, para evitar problemas de
garantia.

En debian los driver se instalan a mano, sin grandes dificultades, lo único que ocurre es que con cada actualización del kernel (no son muy frecuentes)hay que reinstalarlos

su
apt-get install module-assistant build-essentials
m-a build nvidia
m-a install nvidia
dpkg-reconfigure xserver-xorg **(seleccionas nvidia)**

En la actualizacion del kernel solo hace falta

m-a build nvidia
m-a install nvidia


Hola. Finalmente compré un NVIDIA GForce 6800. Cuando tipeo la primera línea para instalar los drivers, me dice: 
No se ha podido localizar el paquete build-essentials

Estoy dando vueltas y no puedo instalar la susodicha placa. 
Agradecería mucho un poco de ayuda. 
Saludos,

---

### Post by gmunioz on 2011-03-22
1- Debes estar conectado a Internet.
2- Simplemente pulsa en: Sistema - Administración - Controladores de hardware
3- Instala el driver sugerido.

Esto es en Ubuntu.

En Debian debes instalar los paquetes que te solicite, mediante apt-get

su
apt-get install module-assistant build-essentials
m-a build nvidia
m-a install nvidia
dpkg-reconfigure xserver-xorg (seleccionas nvidia)

si no lo encuentra es porque estas desconectado de internet o no has habilitado
los repositorios descomentandolos del archivo /etc/apt/sources.list

Este es un ejemplo del archivo:

deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) stable main contrib non-free
deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) stable main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) stable/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) stable/updates main contrib non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main non-free
deb [http://rarewares.org/debian/packages/stable/](http://rarewares.org/debian/packages/stable/) ./
deb [http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/) ./ 
deb-src [http://wine.sourceforge.net/apt/source/](http://wine.sourceforge.net/apt/source/) ./
deb [http://www.fbriere.net/debian/dists/stable](http://www.fbriere.net/debian/dists/stable) ./ 
deb-src [http://www.fbriere.net/debian/dists/stable](http://www.fbriere.net/debian/dists/stable) ./

Te sugiero visites a esdebian
[www.esdebian.org](www.esdebian.org)
Lee mucho, antes de intentar preguntar en ese foro

---

