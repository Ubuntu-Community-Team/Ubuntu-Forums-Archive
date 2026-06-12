---
title: "Problema de instalacion Ubuntu"
date: 2008-11-11
forum: Hardware
---

### Post by PiolaBagio on 2008-11-11
Hola que tal usuarios Linuxeros
Voy directo al grano de mi problema.
La cosa es asi:

Bajo el .iso todo bien de Ubuntu 8.10 lo grabo sin problemas, reinicio mi pc, entra a la pantalla donde se elige idiomas, elijo mi idioma, y ponga probar ubuntu o ponga instalar ubuntu, pone la otra pantalla con el logo UBUNTU y la barra naranja abajo que va y viene de izquierda a derecha. Una vez que deja de ir y venir, que es cuando empieza a cargar, carga un poco y se traba por completo (carga 2 cuadrados y se cuelga).
Probe con todo lo que existe en internet, y no logro conseguir que funcione, lei que puede ser el cd mal grabado, entonces fui a otra PC, y funcionó, lo instale y todo bien. Entonces me puse a desarmar mi pc parte por parte probando que podia ser, saque la placa de video, la de sonido, la disketera, una de mis lectoras, y no funciono, probe todos los codigos que existen (los de apretar F6) y tampoco funcionó..
Me tiene preocupado y muy aburrido no poder instalarlo.
Espero que puedan ayudarme.
Aca les dejo los datos de mi pc:

Intel Inside Celeron D 2.6
Memoria Kingstone 512mb (en 1 slot)
Disco duro de 80 Gb
Placa madre Asrock P4i45GV R.5

PD: No me anda la salida de teclado, entonces uso un teclado USB, el cual puedo utilizar bajo DOS.

Cualquier duda que tengan preguntenme, estoy a su disposicion con tal de instalarlo.

Se agradece cualquier comentario y pido disculpas por hacerles perder su tiempo en mi.

Los saluda atte. PiolaBagio

---

### Post by Hei Ku on 2008-11-11
Si ya probaste de ponerle noapic al iniciar, entonces te diría que pruebes con el Alternate CD, que tiene una instalación en modo texto, pero anda mejor.

---

### Post by PiolaBagio on 2008-11-11
> **Hei Ku said:**
> Si ya probaste de ponerle noapic al iniciar, entonces te diría que pruebes con el Alternate CD, que tiene una instalación en modo texto, pero anda mejor.

Me darias un link por favor? Que no sea torrent, te lo agradeceria muchisimo, gracias por tu respuesta.

Pd: Si ya probe poner noapic, tambien pnpbios=off, tambien acpi=off, tambien, tambien, tambien..

Gracias y por favor Ayuda!

---

### Post by Hei Ku on 2008-11-11
Este es el link a la iso de un servidor en Argentina.

[http://ubuntu.patan.com.ar/release/intrepid/ubuntu-8.10-alternate-i386.iso](http://ubuntu.patan.com.ar/release/intrepid/ubuntu-8.10-alternate-i386.iso)

---

### Post by PiolaBagio on 2008-11-11
> **Hei Ku said:**
> Este es el link a la iso de un servidor en Argentina.

[http://ubuntu.patan.com.ar/release/intrepid/ubuntu-8.10-alternate-i386.iso](http://ubuntu.patan.com.ar/release/intrepid/ubuntu-8.10-alternate-i386.iso)

Ya la habia bajado esa y nada, esa directamente ni podia bootear el cd :(

---

### Post by hictio on 2008-11-11
Lo probaste al CD con el 'Check CD for defects'?

---

### Post by Hei Ku on 2008-11-12
> **PiolaBagio said:**
> Ya la habia bajado esa y nada, esa directamente ni podia bootear el cd :(

Estas seguro que se grabo bien? El mecanismo de booteo es igual para los 2 CDs.

---

### Post by mixed on 2008-11-24
que no te ande el teclado fijate desde bios . si tenes habilitado el legacy support usb. 

es lo mas comun ese problema.

---

### Post by vk-cdg on 2008-11-24
Yo tuve un problema similar en la notebook (finalmente volví a Hardy porque la necesito para dar un recuperatorio). 
En mi caso si dejo presionado el enter o la barra espaciadora, termina de arrancar, digamos coloquialmente que la barrita sigue creciendo y ubuntu termina de cargar.

No le dediqué tiempo a investigar por que y como solucionarla, ya que como dije antes volví a instalar Hardy porque tengo que rendir un recuperatorio y necesito la PC.

---

