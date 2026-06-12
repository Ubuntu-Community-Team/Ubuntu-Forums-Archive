---
title: "Instalacion de ubuntu, sin CDs ni USB"
date: 2009-07-17
forum: Instalación y Actualización
---

### Post by benja22 on 2009-07-17
Hola, en un computador quiero unstalar ubuntu pero no tengo lector de cd,
Como puedo instalarlo??? (sin usar USB)
se puede copiar todos los archivos del cd de ubuntu al disco duro e isntalarlo desde ahi??

gracias:)

---

### Post by moreback on 2009-07-18
¿Qué clase de equipo es que no tiene USB? Lejos la mejor opción es hacerlo por USB si es que no tienes acceso a un lector.

Saludos.

---

### Post by benja22 on 2009-07-18
> **moreback said:**
> ¿Qué clase de equipo es que no tiene USB? Lejos la mejor opción es hacerlo por USB si es que no tienes acceso a un lector.

Saludos.



esque mi USB no esta muy bueno, pero se puede copiar todos los archivos del CD al disco duro e instalarlo desde ah???

---

### Post by Carlos C on 2009-07-18
¿es un laptop? ¿sólo tienes un puerto usb? Lo que no entiendo es cómo vas a copiar los archivos al disco duro si no funciona el usb ni el lector de cd ¿Por la red?

---

### Post by kamus on 2009-07-18
> **benja22 said:**
> esque mi USB no esta muy bueno, pero se puede copiar todos los archivos del CD al disco duro e instalarlo desde ah???

Pero si tienes bueno tu lector no tendria sentido NO instalarlo desde el CD?, de todas maneras no se si venga al caso pero de todas maneras puedes revisar: 

[1]https://help.ubuntu.com/community/Installation/LocalNet

Salu2

---

### Post by benja22 on 2009-07-18
1º No tengo lector, no lee, lo he arreglado (apretando el tornillo) varias veces y ya esta muy gastado

2º No tengo pendrive de 1 gb y ademas el pc no reconoce al inicio algo bootteable por usb

3º Yo una vez copie del cd de win xp todos los archivos al disco duro, luego aprete doble click en setup.exe y lo instale sin problemas. ¿¿Puedo hacer eso con ubuntu???



Saludos

---

### Post by Carlos C on 2009-07-18
> **benja22 said:**
>  3º Yo una vez copie del cd de win xp todos los archivos al disco duro, luego aprete doble click en setup.exe y lo instale sin problemas. ¿¿Puedo hacer eso con ubuntu???
Esto es lo que no entiendo ¿Cómo vas a copiar los archivos? ¿Por la red??? Si es así lo mejor es que veas el enlace que te puso kamus. No es tan fácil como copiar los archivos al disco duro y hacer doble click. ¿Qué sistema operativo tienes instalado?
Faltan datos porque no se entiende bien la situación.
Saludos.

---

### Post by benja22 on 2009-07-18
> **Carlos C said:**
> Esto es lo que no entiendo ¿Cómo vas a copiar los archivos? ¿Por la red???

Si, por red quiero copiar los archivos del cd a mi disco duro [ej: Desde F: (CD) a  E:\Ubuntu(Disco duro)]y despues en esa carpeta hacer doble click en wubi.exe (ese .exe sale en mi cd) y instalarlo. ¿¿Esto se puede hacer??

Y quiero aclarar otro punto: Lo quiero hacer por red LAN desde un notebook a mi pc por lo que no puedo cambiar el lector de cd hacia el pc.

tengo instalado ubuntu pero en el pc que quiero instalarlo esta win xp
saludos

---

### Post by gmunioz on 2009-07-18
Hola ben...:

Necesitas: linld097 un disquete booteable de FreeDOS y la imagen.iso de Ubuntu.

Crea una partición fat de 1.2 gigas.

Descomprime la imagen de ubuntu y cópiala en c:\ con todos sus directorios

Copia linld al disco c:\

Inicia con un disquete de arranque de FreeDOS

Pasa al disco c:\ y ejecuta:

linld097 image=c:casper\vmlinuz initrd=c:casper\initrd.gz &#8220;cl=boot=casper root=/dev/ram rw&#8221; 
     
Se iniciará automáticamente el LiveCD de Ubuntu y ya podrás comenzar la

instalación como si se hubiese arrancado desde el CD, en el resto del 

disco sin particionar

en caso de ser alguna otra versión de Ubuntu como el Alternate CD solo hay que 

localizar el directorio en donde se encuentran los archivos vmlinuz y initrd.gz y 

sustituir el directorio en el comando de inicio. 

sitios de descarga:

Disquete de arranque de FreeDOS
      
[http://www.fdos.org/bootdisks/autogen/FDSTD.144.imz](http://www.fdos.org/bootdisks/autogen/FDSTD.144.imz)

linld097

[http://troglobit.com/files/linld/linld097.com](http://troglobit.com/files/linld/linld097.com)

---

### Post by agustinflames on 2009-07-20
una joya el post el anterior de gmunioz.
Exacto, es necesario bootear un OS desde otro lado

---

### Post by benja22 on 2009-07-28
Gracias :D:D:D

---

### Post by mgonnet3 on 2009-11-29
Hola, yo segui esas instrucciones pero cuando llamo al linld097, me aparece el siguiente error, alguien sabe como solucionarlo?
**[SIZE=1][B]I need 386+ CPU**** in real mode or under VCPI manager**[/SIZE][/B]

---

