---
title: "[SOLUCIONADO] Problema en Jaunty con audifonos en notebook vaio VGN-NR350FE"
date: 2009-05-26
forum: Hardware
---

### Post by Naldylipu on 2009-05-26
Hola!
Tengo instalado el Ubuntu 9.04 en un Vaio VGN-NR350FE, el cambio ha sido bastante bueno y he aprendido a hacer varias cosas en estas semanas, pero no puedo encontrar por ninguna parte como arreglar este problema, al conectar los audifonos el sonido sigue saliendo por los parlantes al mismo volumen que estaban saliendo, uso un headset y el micrófono funciona bien, al usar windows los audifonos y el micrófono funcionan, espero puedan ayudarme.

Saludos!!

Edit: perdón por poner el thread acá, aun estoy conociendo este foro y no encontraba la sección correspondiente

---

### Post by Carlos C on 2009-05-26
Ningún problema, lo movemos al subforo adecuado.

Sobre tu problema, es común en algunos modelos Vaio. Te sugiero una manera que ha funcionado antes, tienes que editar tu archivo alsa-base.conf:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Al final del archivo añade la siguiente linea: 
```
options snd-hda-intel model=sony-assamd
```
Luego graba los cambios, cierra el archivo, reinicia y prueba nuevamente.

---

### Post by Naldylipu on 2009-05-26
Muchas gracias :) me funciona perfecto ahora

---

### Post by Tato2008 on 2011-11-22
> **Carlos C said:**
> Ningún problema, lo movemos al subforo adecuado.
 
Sobre tu problema, es común en algunos modelos Vaio. Te sugiero una manera que ha funcionado antes, tienes que editar tu archivo alsa-base.conf:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Al final del archivo añade la siguiente linea: 
```
options snd-hda-intel model=sony-assamd
```
Luego graba los cambios, cierra el archivo, reinicia y prueba nuevamente.
 
te agradeceria si me indicaras como proceder dado que Yo tambien tengo el mismo problema pero no encuentro ese archivo para editar. Mi Vaio es una VGNCS270T
Gracias

---

### Post by RafaelG on 2011-12-01
> **Tato2008 said:**
> te agradeceria si me indicaras como proceder dado que Yo tambien tengo el mismo problema pero no encuentro ese archivo para editar. Mi Vaio es una VGNCS270T
Gracias

Estimado Tato2008,

Estas ingresando desde Consula o terminal con el comando entregado por Carlosc ya que posterior a eso te solicitara tu password y recien hay podras ingresar al archivo indicado para posteriormente editarlos.

Saludos cordiales,

---

