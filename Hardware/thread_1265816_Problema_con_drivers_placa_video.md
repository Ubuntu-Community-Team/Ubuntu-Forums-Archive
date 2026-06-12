---
title: "Problema con drivers placa video"
date: 2009-09-13
forum: Hardware
---

### Post by worming on 2009-09-13
Instale hace poco ubuntu 9.04 en mi notebook... y andaba de maravilla, excepto por un par de "problemas"... 

El primero es que instale los drivers de la placa de video que es una ATI HD 3200...
segun lei en la guia de instalacion proporcionada por ATI, habia que ejecutar el archivo .run que descargabamos 

_Tambien decia esto:_
[I]The following packages must be installed in order for the Catalyst™ Linux driver to
install and work properly:
-XFree86-Mesa-libGL
-libstdc++
 -libgcc
 -XFree86-libs
 -fontconfig
 -freetype
 -zlib
 -gcc[/I]
Que no tengo idea que son esos paquetes... (no se si los tengo o no)

y luego segun la version de x.org tenias que ejecutar un comando de configurarion
[I]For versions of X.Org newer than 7, /usr/bin/aticonfig --initial to configure the
driver for your ATI product.
For versions of X.Org older than 7, /usr/X11R6/bin/aticonfig --initial to configure
the driver for your ATI product.
[/I]
Instale todo perfecto pero a la hora hacer*/usr/bin/aticonfig --initial* me tiraba un error...

Reinicie y desde ese momento cdo habro una ventana de firefox, o lo que fuere se nota que anda mal el tema de lo grafico... se ve muy lento, se demora mucho en refrescar...

Entonces necesito saber... 
Como volver a los genericos que traia desde un principio que me andaban bien pero no me dejaban poner los efectos extra de apariencia...
O que alguien que me ayude a instalar bien los drivers de mi placa asi me queda andando...

el segundo es que cuando apago, reinicio, la notebook emite un ruido extraño por los parlantes como si el apagado hubiese sido producido por un corte de energia y no por la solicitud mia...

Saludos y Gracias

---

### Post by Hei Ku on 2009-09-13
tenes que poner:

sudo aticonfig --initial

Probablemente te tiró un error porque no tenías permiso de escritura sin el sudo.

Segundo, hay una guía especial para Ubuntu Jaunty, no sé si fue esa la que seguiste:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Si no es así, postea el link a la guía que utilizaste.

---

### Post by worming on 2009-09-13
Esta es la "guia" que da ati en su pagina oficial...
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf)

sudo aticonfig --initial asi lo hice... con sudo

Pero igual ya lo pude solucionar!...
no me preguntes como pero fue algo asi...
para que le sirva a alguien
Baje el compiz fusion lo agregue al inicio
y en la terminal puse 
sudo aptitude install fusion-icon

Gracias igual!

---

