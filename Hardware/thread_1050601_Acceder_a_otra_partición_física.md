---
title: "Acceder a otra partición física"
date: 2009-01-25
forum: Hardware
---

### Post by Ropoo on 2009-01-25
Hola. Hoy instalé Ubuntu 8.10. 
Tengo un disco 32 gb(ahí esta instalado el SO) y otro de 200.
Me gustaría saber como puedo acceder al segundo, que tiene archivos importantes que tenía en Windows.

Gracias de antemano.

---

### Post by staar on 2009-01-25
hola, si son archivos de windows supongo que el sistema de archivos sera NTFS, en ese caso ubuntu no monta la particion automaticamente (el sistema de archivos de linux es diferente y no es como windos con C:, D:, etc, las particiones y discos se montan en "carpetas") la forma mas facil de montar tu disco es yendo a Lugares -> Equipo , y ahi te va a aparecer un icono de tu disco, click derecho sobre el, montar el volumen y listo :D

otra cosa, ubuntu por defecto no monta automaticamente las particiones NTFS al inicio, asi que al reiniciar vas a tener que volver a montarlas (OJO, este comportamiento puede cambiarse)

saludos

---

### Post by Ropoo on 2009-01-26
Gracias por la ayuda. Pero tube un problema más:

[IMG]http://img228.imageshack.us/img228/8207/capturaaui6.gif[/IMG]

Por lo que tube que hacer [esto]("http://www.guia-ubuntu.org/index.php?title=Acceso_a_particiones_Windows").

---

### Post by staar on 2009-01-26
esta muy bien lo que hiciste (a eso me referia con que puede cambiarse ;) ) es la forma mas "hard" :P, el mensaje que te salio es porque windows no cerro bien la ultima vez, y el sistema de archivos quedo "sucio", son las limitaciones de un sistema de archivos obsoleto como es NTFS, que se le va a hacer...

saludos

---

