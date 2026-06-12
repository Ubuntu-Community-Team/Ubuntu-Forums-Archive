---
title: "BIOSTAR and Ventilators, PROBLEM!!"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by YingYang on 2005-07-01
Hello everybody,

I would like to consult here my problem.
My computer is an AMD Sempron 2400 with a BIOSTAR Mother Board (Chipset KM400A). I have installed an Ubuntu with kernel 2.6.10 and my problem are the ventilators. They run with the maximun power always and the noise is maximun. They don't control the temperature. It's different with Windows XP, because the drivers that I have installed control the ventilators correctly.
I looked for linux drivers in the official BIOSTAR web but it doesn't exists. I have proved to recompile the kernel ... and nothing. I don't know what more I can do, and I would like to know if more AMD and BIOSTAR users have the same annoying problem.

Somebody can help me, please?

Thank you very much.
Bye!

---

### Post by intangible on 2005-07-01
Look into "athcool" but it's not 100% stable on some computers (mine anymore :( it was stable on an older bios tho )

---

### Post by YingYang on 2005-07-03
Hello intangible!

I can't install athcool because I don't have libc6 2.3.2.ds1-21:

$ dpkg -i athcool_0.3.10-2_i386.deb
(Leyendo la base de datos ...
65536 ficheros y directorios instalados actualmente.)
Preparando para reemplazar athcool 0.3.10-2 (usando athcool_0.3.10-2_i386.deb) ...
Desempaquetando el reemplazo de athcool ...
dpkg: problemas de dependencias impiden la configuración de athcool:
 athcool depende de libc6 (>= 2.3.2.ds1-21); sin embargo:
  Versión de libc6  en el sistema es 2.3.2.ds1-20ubuntu13.
dpkg: error al procesar athcool (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 athcool

What can I do now??

---

### Post by intangible on 2005-07-05
The easiest way is to add the universe repositories and install it through Synaptic.  [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)  Or download it from [http://packages.ubuntu.com](http://packages.ubuntu.com)

It looks like you downloaded the athcool from the debian repositories.

---

