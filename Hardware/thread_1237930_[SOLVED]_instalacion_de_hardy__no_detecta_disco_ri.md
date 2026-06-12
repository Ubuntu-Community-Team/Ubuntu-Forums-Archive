---
title: "[SOLVED] instalacion de hardy  no detecta disco rigido"
date: 2009-08-11
forum: Hardware
---

### Post by LolaMora on 2009-08-11
Hola :)
Necesito instalar Ubuntu en las PCs del colegio donde trabajo. 
Nos interesa cambiar un poco la mentalidad windows-dependiente que existe.

Las PCs tienen WinXP. Los discos estan desfragmentados y frizados (deep freeze)

Les cuento lo que hice:
- desinstale totalmente el deep freeze
- puse el cd para instalar Ubuntu 9.04
- cuando llega a la pantalla para gestionar las particiones no sale nada, esta vacia.

Me meti al escritorio Ubuntu con el live CD, abri gparted y sale que no se encuentran dispositivos y la ventana de particionhes esta vacia.

Me fui al BIOS y el disco rigido figura como "third master" IDE.

Hemos abierto la PC y es un disco SATA de 80 gigas.

Tendra algo que ver esto con el hecho que no detecta el disco rigido durante la instalacion?
Que puedo hacer para Linux?

Hace algun tiempo atras le instale el Ubuntu 7.10  a una de ellas para probarlo y recuerdo que se instalo sin ningun problema. Pero con Hardy no es asi.

Por lo que estuve googleando, adverti que hay gente con problemas "similares", pero no publican la solucion.

Alguna idea?


[COLOR="Black"]_La solucion esta_[/COLOR] en escribir en la linea de opciones al iniciar la instalacion (con F6) lo siguiente:

pci=nomsi

---

### Post by staar on 2009-08-11
faltó el dato más importante, que motherboard es?

saludos

---

### Post by guillermolisi on 2009-08-12
La unidad de CD esta como master ? Si es asi, de que canal ?
Se puede hacer que el BIOS vea el disco como Master del primer canal IDE ?

---

### Post by LolaMora on 2009-08-12
> **staar said:**
> faltó el dato más importante, que motherboard es?

saludos

La placa es una

Asus A8V-MX  Rev. 0405

---

### Post by LolaMora on 2009-08-12
> **guillermolisi said:**
> La unidad de CD esta como master ? Si es asi, de que canal ?
Se puede hacer que el BIOS vea el disco como Master del primer canal IDE ?

El Dvd esta detectado como Primary Master Ide en el BIOS y esta conectado al canal IDE 1 de la placa madre.

EL HD tiene cable SATA, esta detectado como Third Master IDE y esta conectado al canal SATA 1 de la placa madre.

---

### Post by staar on 2009-08-12
googleando un poco, encontré que hay un bug con esa placa, y existen dos posibles soluciones, ambas implican modificar la línea de booteo del kernel en el grub y agregar un parámetro...

arrancá con el livecd, después de seleccionar el idioma, apretá F6 y agregá a la línea el parámetro *all_generic_ide* después intentá instalar ubuntu, en teoría te tendría que reconocer el disco, una vez instalado tendrías que, desde el mismo livecd, sin reiniciar (porque si lo haces vas a tener de nuevo el problema), modificar el /boot/grub/menu.lst de la nueva instalación, identificar la línea que llama al kernel (al final, dentro de la primera entrada de ubuntu, la línea que empieza con  *kernel* y termina con *ro quiet splash*) y agregar el mismo parámetro *all_generic_ide*

el problema con esta solución es que, aparentemente, el sistema instalado funciona muy lento, no como debería, para evitar esto parece que, en vez de usar el parámetro *all_generic_ide*, se tiene que usar *pci=nomsi*

saludso

---

### Post by LolaMora on 2009-08-13
> el problema con esta solución es que, aparentemente, el sistema instalado funciona muy lento, no como debería, para evitar esto parece que, en vez de usar el parámetro *all_generic_ide*, se tiene que usar *pci=nomsi*


Lo he solucionado de la manera que vos me sugeriste, escribiendo en el comienzo de la instalación

pci=nomsi

He accedido a las particiones, las edite y las cree convenientemente. 
El arranque del SO fue normal, bastante rápido por lo que veo.
No necesite editar el menu.lst

Gracias Staar por tu ayuda.

---

### Post by Fistandantilus on 2009-08-15
Me hiciste acordar a mi, tenia el mismo problema, [http://ubuntuforums.org/showthread.php?t=1191165](http://ubuntuforums.org/showthread.php?t=1191165)

Me alegro que lo hayas podido solucionar, Suerte.

PD: (offtopic) de que colegio estas hablando??? de monte grande? naci en luis guillon... :)

---

### Post by LolaMora on 2009-08-16
> **Fistandantilus said:**
>  PD: (offtopic) de que colegio estas hablando??? de monte grande? naci en luis guillon... :)


El colegio donde trabajo queda en Capital
Mi zona de residencia es Monte Grande

---

### Post by guillermolisi on 2009-08-16
> **LolaMora said:**
> El colegio donde trabajo queda en Capital
Mi zona de residencia es Monte Grande
Me alegro que el tema este solucionado y mas si se conocen, pero por favor las cuestiones personales/sociales via PM (private message). Gracias !

---

