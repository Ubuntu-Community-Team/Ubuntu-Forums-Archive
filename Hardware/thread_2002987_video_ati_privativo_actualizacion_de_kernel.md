---
title: "video ati privativo actualizacion de kernel"
date: 2012-06-13
forum: Hardware
---

### Post by zaret on 2012-06-13
hola la verdad estoy usando ubuntu 12.04, use hace un tiempo kubuntu, pero me cambie debido a un problema con la tarjeta de video una radon hd4550, una ves instalado el driver privativo se actualizo el kernel para lo cual el driver privativo deja de funcionar como corresponde... a lo cual se supone que se ha de reinstalar, pero en esta versión de ubuntu no me fue posible hacerlo a través del modo de recuperación, debido a que me monta el sistema de archivos en modo de solo lectura.... ahora que ubuntu me pide actualizar el kernel... quiero saber si a alguien mas le ha pasado y tiene una solución para lo de el montaje de solo lectura para pasar a tener permisos de escritura etc.... saludos

---

### Post by silex89 on 2012-09-15
Hola :)

Por desgracia, AMD/ATI dejó de prestar soporte para todas las tarjetas gráficas menores que la serie HD5000 (vale decir, desde la HD1000 a la HD4000). Es por eso que Catalyst ya no funcionará con tu tarjeta gráfica.

Yo uso ArchLinux, y en esa distro hay una versión especial de Catalyst llamada Legacy (la estoy usando ahora) y es básicamente el mismo driver pero con soporte especializado para las tarjetas que ATI dejó de soportar. Seguramente existe un paquete para Ubuntu (o un PPA, no lo sé) para que lo puedas instalar.

Mucha suerte! :D

---

