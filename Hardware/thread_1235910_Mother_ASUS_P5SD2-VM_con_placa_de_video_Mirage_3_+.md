---
title: "Mother ASUS P5SD2-VM con placa de video Mirage 3 + integrada en chip SIS672"
date: 2009-08-09
forum: Hardware
---

### Post by jvgonza on 2009-08-09
Tengo una Mother ASUS P5SD2-VM con placa de video Mirage 3 + integrada en chipset SIS672.

Soy nuevo en Ubuntu.  Instale la version 9.04 y tengo problemas en el reconocimiento de esta placa de video. No puedo ponerla a mas de 1024x768. Probe instalar distintos drivers que encontre en distintos foros pero no consegui lo que esperaba.
Les agradeceria si pueden darme alguna sugerencia.

Saludos y gracias.

---

### Post by rubioo on 2009-08-09
Yo tengo ese mother y nunca tuve problemas :confused:

---

### Post by guillermolisi on 2009-08-09
> **jvgonza said:**
> Tengo una Mother ASUS P5SD2-VM con placa de video Mirage 3 + integrada en chipset SIS672.

Soy nuevo en Ubuntu.  Instale la version 9.04 y tengo problemas en el reconocimiento de esta placa de video. No puedo ponerla a mas de 1024x768. Probe instalar distintos drivers que encontre en distintos foros pero no consegui lo que esperaba.
Les agradeceria si pueden darme alguna sugerencia.

Saludos y gracias.
Date una vuelta [por este thread]("http://ubuntuforums.org/showthread.php?t=660167&highlight=SIS+672&page=7")

En el post 64 hay alguien que llevo a cabo un procedimiento para mejorar la resolucion de una maquina con el mismo chip de video que el tuyo.

Ese thread es largo, 77 mensajes, pero vale la pena.

Espero te sea de utilidad.

---

### Post by jvgonza on 2009-08-09
> **guillermolisi said:**
> Date una vuelta [por este thread]("http://ubuntuforums.org/showthread.php?t=660167&highlight=SIS+672&page=7")

En el post 64 hay alguien que llevo a cabo un procedimiento para mejorar la resolucion de una maquina con el mismo chip de video que el tuyo.

Ese thread es largo, 77 mensajes, pero vale la pena.

Espero te sea de utilidad.



Muchas Gracias por las indicaciones.  
Pude mejorar mi situacion.  Comence a hacer lo que me indicastes y en si con esto no lo pude solucionar porque a la hora de instalar displayconfig-gtk me decia que no estaba disponible para la instalacion en la version 9.04.

Tus indicaciones me sirvieron para encontrar una solucion.

Aparentemente la aplicacion displayconfig-gtk no esta incluida en la version 9.04.

Lo que hice lo encontre en el siguiente link:

[http://www.guia-ubuntu.org/index.php?title=Olivetti_520](http://www.guia-ubuntu.org/index.php?title=Olivetti_520)

Descargue los drivers de la SiS671 desde aqui:  [http://launchpadlibrarian.net/24529643/xorg-driver-sis671_0.9_i386.deb](http://launchpadlibrarian.net/24529643/xorg-driver-sis671_0.9_i386.deb) 
 

Mi chipset es el 672 pero ambos tienen la misma tarjeta de video integrada.


Los instale ejecutando el archivo y luego reconfigure el xorg con: 
  $ sudo dpkg-reconfigure -phigh xserver-xorg
 Reinicie y luego se habilitaron mas resoluciones para seleccionar.


La aceleracion grafica no esta habilitada pero por lo que estuve leyendo no se si puede habilitarse con esta placa.


Igualmente voy a seguir investigando para ver si puedo mejorar mas aun.


Muchas gracias por la ayuda.


Saludos!


Javier

---

