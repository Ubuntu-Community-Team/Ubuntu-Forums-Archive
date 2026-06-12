---
title: "pantalla negra"
date: 2012-12-21
forum: Hardware
---

### Post by lord_knox on 2012-12-21
hola a todos, estoy tratando de instalar ubuntu 10.4 en un pentium dualcore. el tema es que lo intalo bien pero cuando reinicio me tira pantalla negra. imposible entrar al grub, consola externa, entorno grafico, nada de nada. lo intale 5 veces intentando de todo en internet y no se puede. el tema esta con el nomodeset que lo saco antes de instalar para que el entorno grafico ande. pero depues parece que lo vuelve a agarrar... nunca me paso algo asi. a ver si alguien puede darme una mano, porque si no hay solucion sale de nuevo winc***a.

saludos

---

### Post by guillermolisi on 2012-12-23
Por que 10.04 y no 12.04 ?
Que motherboard estas usando ?
Que placa de video estas usando ?

Para que la opcion "nomodeset" quede permanente hay que configurarlo dentro de las opciones por defecto del Grub para la imagen del kernel que utilices. Si se modifica en tiempo de arranque, es valida solo para ese momento y en el proximo reboot se pierde.

---

