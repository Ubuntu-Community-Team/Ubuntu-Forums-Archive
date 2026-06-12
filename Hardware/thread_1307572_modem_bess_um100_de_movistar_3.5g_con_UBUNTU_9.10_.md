---
title: "modem bess um100 de movistar 3.5g con UBUNTU 9.10 KARMIC"
date: 2009-10-31
forum: Hardware
---

### Post by salensaturn on 2009-10-31
Estimados Amigos, tengo el modem bess um100 de movistar 3.5g (Venezuela)

Estoy tratando de INSTALARLO utilizando la guia de 'http://www.forat.info/2008/04/20/como-instalar-el-escritorio-movistar-modem-usb-mc950d-en-linux-ubuntu/'

sin embargo cuando ACTUALIZO los repositorios de SYNAPTIC, obtengo el siguiente error:

[COLOR=Red]Imposible obtener [http://open.movilforum.com/archive/escritorio-movistar/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://open.movilforum.com/archive/escritorio-movistar/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/COLOR]

Por lo que sudo gedit  /etc/apt/sources.list y cambie KARMIC por JAUNTY, logra actualizar y descargar la APLICACION escritorio-movistar, pero luego cuando trato de instalar el paquete me arroja un error de que depende de  [COLOR=Blue] python-webkitgtk[/COLOR]

por lo que efectue un  sudo apt-get install python-webkitgtk

pero me arroja 'El paquete python-webkitgtk no tiene candidato para su instalación'

estuve revisando por alli y veo que el python-webkit es el reemplazo actual, pero NO LOGRE de ninguna forma instalar la aplicacion, veo que la unica posibilidad es conseguir el paquete [COLOR=Red]http://open.movilforum.com/archive/escritorio-movistar/ubuntu/dists/karmic/main/binary-i386/Packages.gz[/COLOR]

alquien me puede ayudar con esto?

o si saben alguna otra manera de instalar ese MODEM

muchas gracias
bye
Pablo

---

### Post by estebanf on 2009-11-15
Puedes conseguir el paquete transitorio en [http://mirrors.kernel.org/ubuntu/pool/universe/p/pywebkitgtk/python-webkitgtk_1.0.2-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/p/pywebkitgtk/python-webkitgtk_1.0.2-1ubuntu1_i386.deb)

estebanf.com

---

### Post by edelcid on 2009-12-06
De todas formas, prueba instalando una "nueva conexión" desde el Gestor de Redes. Por ahí, te toma al modem y la conexión. Cuidado con el nombre del APN, usuario y contraseña, que pueden no ser los que coloca Ubntu por defecto.

---

