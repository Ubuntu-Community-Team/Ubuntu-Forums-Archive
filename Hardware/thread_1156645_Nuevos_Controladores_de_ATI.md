---
title: "Nuevos Controladores de ATI"
date: 2009-05-11
forum: Hardware
---

### Post by Applelnx on 2009-05-11
Hola, estaba viendo que salieron los nuevos controladores de ATI y me dijeron que eran buenos. Mi pregunta es simple pero clave (porque siempre alguna me mando).

En caso de que falle algo de la instalacion, y tenga que ingresar por el modo recuperacion, como vuelvo a cero en la parte grafica? O sea, como vuelvo a la configuracion default de la placa de video?

Esta es la guia que me baje desde ATI

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat94-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat94-inst.pdf)

Y la pagina es esta:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

Saludos :D

---

### Post by Hei Ku on 2009-05-12
Yo los instalo generando un paquete .deb y despues instalando esos. Si fallan, desinstalo esos paquetes y vuelvo a instalar los que tenía. Siempre anduvo tudo bem, tudo legal!

Y en cuanto a como andan, varian muchisimo por modelo de placa. Algunos andan barbaro, otros un desastre, y varia de version a version. Yo me tuve que saltear versiones del driver porque ni arrancaba. Y ahora se que muchos tienen dramas, pero a mi la 9.4 me anduvo joya. :S

---

### Post by Applelnx on 2009-05-12
Hola Hei Ku, gracias por responder. Tendre que probar los nuevos para ver. 

El problema es que no quiero hacer nada sin saber como revertirlo. La duda que tengo es como desinstalar los controladores que instalo...

Y si no funcionan y no arranca como hago para desintalarlos y tener la configuracion de video original desde la consola de recuperacion?

Ya me ha pasado que no arrancaba y la unica que me quedo fue reinstalar todo ubuntu :(

EDIT: encontre algo, para hacer un backup:
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp

Y para recuperar:
# cp /etc/X11/xorg.conf.bkp /etc/X11/xorg.conf

---

