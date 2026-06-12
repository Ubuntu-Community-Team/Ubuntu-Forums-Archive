---
title: "Cree una particion fat32 porque tengo un doble booteo w7 y ubuntu pero no funciona"
date: 2014-04-11
forum: Hardware
---

### Post by rafael9 on 2014-04-11
Hola a todos todas aficionados y expertos, primero que nada quiero decir que yo soy un aficionado a la informatica y que no se nada de consola y que instale este SO porq mg y me va rapido.
Queria saber si me pueden ayudar con este pequeño problema: me cree una particion fat32 de 27 GB para poder acceder a ella tanto desde Windows 7 o Ubuntu 12.04.
Ya que yo soy una persona que suele jugar a juegos de windows no quise eliminarlo bueno las caracteristias tecnicas no las tengo demasiado especifias:

Procesador: Intel 2 nucleos 1.6 Ghz
Grafica: Integrada capacidad de almacenamiento 128 MB
Ram: DDR3 2 GB

y aqui las caracteristicas de software

SO instalado: Ubuntu 12.04 (bien actualizado) y Windows 7 home basic, doble booteo utilizando GNU GRUB
 
Particiones: 
primaria: recuperador de windows 2 GB aprox    formato ntfs
                     
primaria: Windows 7 home basic  341 GB         formato ntfs
                     
primaria: Ubuntu 12.04    87 GB formato      ext4
                     
Extendida:
                                     Logica: Linux Swap                8 GB formato     ext4
                                     
Logica: Archivos formato       27 GB formato     fat32

Bueno mi problema es que no me mota correctamente la particion fat32 y no me deja acceder a ella cada vez que lo intento me salta u error que dice exactamente esto 

No se pudo montar ARCHIVOS

mount: el dispositivo especial UUID=14F8-171C no existe

lo curioso es que de windows no tengo problema para acceder a ella y antes de que me digan que revise si tengo la carpeta media si la tengo.

por cierto de paso queria saber cuanto me recomiendan de Swap para mi compu para darles una idea soy el clasico multitarea que tiene 20 cosas abiertas a la vez por ejemplo:
quemo un cd mientras bajo musica o algun programa en el centro de software y mientras se hacen estas tareas hablo por skype y tambien estoy ugando algun juego liviano

Muchas gracias anticipadas por su gran ayuda C:

---

