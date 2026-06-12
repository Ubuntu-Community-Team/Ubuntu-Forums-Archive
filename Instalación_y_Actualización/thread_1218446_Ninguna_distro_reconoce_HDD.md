---
title: "Ninguna distro reconoce HDD"
date: 2009-07-20
forum: Instalación y Actualización
---

### Post by agustinflames on 2009-07-20
Hola a todos vuelvo a las canchas
(quizás los más viejos se acuerden de mi ahaha).

El asunto es el siguiente:
Actualmente soy usuario de debian, pero a mi mamá le gusta ubuntu, así que ahora como tengo algo de tiempo libre una tarde de ocio procedí a actualizarle el tarro.

1º Tenía instalado Gutsy
2º Iba a ponerle 9.04 y a la hora de particionar, no encontraba ningún disco duro, es un WD1600AABS (Western Digital).
3º Intenté con Debian Lenny, tampoco, openSUSE 11 tampoco, Debian Etch si lo agarró pero me tiró error de instalación del Grub, mas allá no intenté denuevo, entenderán mi desesperación jaja.
4º Asi que me cambié de unix y finalmente intente con openSolaris y este si funcionó, pero no se porque no me da inet (y sinceramente no me gustó, ni me sé los comandos de consola).

El disco es [sata de la serie caviar blue]("http://www.wdc.com/sp/products/products.asp?driveid=257") de western.

Será algo de los nuevos kernels?
Hay algo que debería saber acerca de los Sata HDD (algo sobre la bios)?
No creo porque ya le he puesto varios linuxes a este tarro.
He googleado y no encuentro solución, asi que recurro a uds que es la comunidad con mas gente.

Saludos cordiales

---

### Post by Patriciologico on 2009-07-20
Se me ocurre que revises la BIOS y veas que los discos estan correctamente configurados como SATA (Configurado como ACHI) y no IDE. Revisa eso y nos cuentas.

Saludos!

---

### Post by jolfig on 2009-08-12
Hay un gran bug en el GRUB que le impide el correcto manejo de los dispositivos SATA.
Intenta instalar Ubuntu con el "alternate disk" y utiliza LILO como gestor de arranque.
Avisa como te fue.

---

### Post by gmunioz on 2009-08-15
Hola agu.....:

Prueba con:

Iniciar con el livecd, después de seleccionar el idioma,

pulsar F6, a continuación agregar la opción:

**pci=nomsi**

---

