---
title: "Problema con kernel 2.6.30-020630-generic y Nvidia 8600 gt"
date: 2009-08-11
forum: Hardware
---

### Post by Just64 on 2009-08-11
Al intentar iniciar con ese kernel tengo un error con el controlador de la placa de video, dice q "fallo al cargar el NVIDIA kernel module".
Inicio el Ubuntu en low-graphics con el kernel del titulo y al tratar de activar el contralor versión 180, no hace nada.

Como hago para actualizar lo drivers de nvidia a los 190.xx?

---

### Post by juancarlospaco on 2009-08-12
Karmic?, te faltan updates, ya va por el 2.6.31.5

---

### Post by gmunioz on 2009-08-12
Hola Jua.....:

Si tienes Jaunty con el kernel 2.6.30, necesitas los

drivers nvidia de Karnic.

Para instalarlos debes hacer pinning.

Para hacer pinning, primero agregas en tu sources list

ejecutando en consola (aplicaciones - Accesorios - Terminal)

sudo gedit /etc/apt/sources.list

El siguiente repositorio de karmic

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted universe multiverse

Luego ejecutas, para actualizar

sudo apt-get update 

A continuación para tener todos los paquetes

necesarios ejecutas

sudo apt-get build-dep nvidia-180-kernel-source

y para generar los paquetes a instalar, ejecutas

luego:

sudo apt-get -b source -t karmic nvidia-180-kernel-source

Esto despues de un tiempo te generará todos los

paquetes .deb necesarios para instalar los drivers

que instalaras, ejecutando en el mismo directorio

sudo dpkg -i *.deb

---

### Post by dirty fingers on 2009-08-13
[http://ubuntuforums.org/showthread.php?t=1188420](http://ubuntuforums.org/showthread.php?t=1188420)

---

