---
title: "Problema con la tarjeta inalambrica usb"
date: 2011-01-08
forum: Hardware
---

### Post by matiasolimpo on 2011-01-08
Hola compañeros, tengo un problema con mi tarjeta inalmbrica usb. Cuando la conecto, aparece un icono en la barra superior derecha al cual le hago el click, el mismo dice "RED CABLEADA" y "REDES INALAMBRICAS", pero este ultimo aparece como desconectado :/
He intentado con los controladores restringidos y no, no hay ninguno, Tambien muchos comandos de internet i otros tutoriales e inclkuso el que viene con ubuntu y no hay caso.

Mi tarjeta de red es una Linksys modelo wusb54gc ver. 3.0.01


Desde ya, muchas gracias por su ayuda.

---

### Post by guillermolisi on 2011-01-09
Que version de Ubuntu estas usando ?
La antena funciona bien en otras maquinas con Linux u otro SO ?

---

### Post by matiasolimpo on 2011-01-10
sisisi, en windows xpercha anda perfecto.

---

### Post by matiasolimpo on 2011-01-11
ubuntu 9.04 es la version

---

### Post by guillermolisi on 2011-01-11
> **matiasolimpo said:**
> ubuntu 9.04 es la version
Alguna razon para no actualizar a la version 10.10 ? En esa version hay grandes mejoras introducidas en el kernel (drivers) que han resuelto muy bien varios inconvenientes con antenas WiFi.

---

### Post by matiasolimpo on 2011-01-12
si, procesador Intel D 2.66 Ghz, memoria ram 448 MB y tarjeta grafica via/s3g unichrome pro igp. 
con la version 10.04 se me congelaba la pantalla, entonces pase a la version anterior y no hubieron mas problemas. si no me anda la 10.04 menos la 10.10 :/
pero bueno, lo unico que quiero es tener internet en ubuntu para abandonar win xp que me tiene harto y pasarme a ubuntu a aprender cosas nuevas

---

### Post by gmunioz on 2011-01-13
Sugerencia:
Intenta con kernels mas modernos, dentro de esa distribución.
Los encuentras aqui:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by matiasolimpo on 2011-01-13
cambiando el kernel me tomará el driver de la tarjeta de red usb?

---

### Post by guillermolisi on 2011-01-13
> **matiasolimpo said:**
> cambiando el kernel me tomará el driver de la tarjeta de red usb?
En general, los drivers de perifericos (con excepcion de impresoras y algunos dispositivos USB) estan incluidos en el kernel, por eso la sugerencia de probar con kernel mas recientes.

De hecho las pruebas que mencione hice usando 10.04.01 con kernel 2.6.35 tenian como objetivo confirmar que algunas antenas USB (externas y/o integradas) funcionaban bien.

---

### Post by matiasolimpo on 2011-01-23
ah okei, muchas gracias.
pero cómo sé a qué version actualizar?

---

