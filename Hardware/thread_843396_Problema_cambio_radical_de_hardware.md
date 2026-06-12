---
title: "Problema: cambio radical de hardware"
date: 2008-06-28
forum: Hardware
---

### Post by temaqueja on 2008-06-28
Hola, quiero saludar aca y agradecer de antemano su ayuda ;)


la historia: hace poco puse ubuntu 8.04 en una placa pcchips 925 celeron 1.7mhz apenas 120mb, red y etc incorporado. Version server porque era el unico de dejarse instalar en ese hardware. Lo tenia dual con xp y todo me iba de maravilla...  hasta que!!

**el problema**: se me ocurrio mejorar el hardware haciendo cambios drasticos y ahora ubuntu no funciona, muestra infinidad de mensajes al iniciar y se cuelga.

El nuevo hardware es placa pcchips p55g + core2duo 2.4 + 2 gigas, red y etc incorporado. como es dual el windows tambien me tiro pantalla azul y tuve q reinstalarlo, luego de eso windows malogro el grub, leyendo en foros encontre esta web: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) me baje de ahi una iso y queme un cd booteable para arreglar grub, desde ahi hay la opcion de cargar linux del pc y me salen los tropecientos mensajes que ya mencione.

Preguntas a uds los entendidos: 
¿tiene solucion o caballero, a instalar de nuevo?

---

### Post by tzulberti on 2008-06-28
Cuando se cambia el procesador de la PC, lo mejor es reinstalar. No se necesario reinstalar por cada cambio de hardware, pero con el procesador tener que reinstalar seguro.

---

### Post by MeduZa on 2008-06-28
> **tzulberti said:**
> Cuando se cambia el procesador de la PC, lo mejor es reinstalar. No se necesario reinstalar por cada cambio de hardware, pero con el procesador tener que reinstalar seguro.

esto es linux, no tienen nada que ver deberia funcionar, capas te falta algo o cambiaste la posicion de los discos, el hardware se detecta en el boteo pero si cambiaste los discos de lugar ya no esta todo como deberia y no anda!

yo cambie de micro y de placa de video sin tener que hacer nada!
el windows le cambias lo que sea y se pudre! tenes que reinstalarlo pero el ubuntu no

---

### Post by Hei Ku on 2008-06-28
La instalacion que tenias tiene algo de particular? tenes algun driver en blacklist o que forzas a cargar en el inicio?
Como dice Meduza, la posicion de los discos es igual?

---

### Post by Mauro22 on 2008-06-28
Si tenes el home aparte, mandale una instalacion fresca.

Acordate de usar los mismos nombres de usuario, asi cuando terminas de instalar, te levanta tu home.

---

### Post by fgl82 on 2008-06-30
Yo no sé cuál puede ser el problema, pero doy fe que cambiando procesador + memoria + mother, no hace falta reinstalar (en Linux, en Windows si, obvio)

---

### Post by temaqueja on 2008-07-04
> **Hei Ku said:**
> La instalacion que tenias tiene algo de particular? tenes algun driver en blacklist o que forzas a cargar en el inicio?
Como dice Meduza, la posicion de los discos es igual?

Pues si solo es un disco, y la posicion biene a ser el unico ide de la p55g (viene con 1 ide y 4 sata), en la placa anterior estaba en el ide principal y el lector de cd en el segundo ide.

Intente varias cosas y no se pudo, al final tuve que optar por volver a instalarlo, eso si: fue mas facil ya q el nuevo hardware ayudo mucho.

Gracias por sus comentarios.

---

