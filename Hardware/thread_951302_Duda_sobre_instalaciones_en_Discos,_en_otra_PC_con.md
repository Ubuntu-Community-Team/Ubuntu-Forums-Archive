---
title: "Duda sobre instalaciones en Discos, en otra PC con distinto Hardware."
date: 2008-10-18
forum: Hardware
---

### Post by pol666 on 2008-10-18
El tema es así mi vieja tiene una computadora maldita que no hay cosa que le ande bien, Y no es algo muy viejo (muy) amd Duron 750Mhz 184Mb ram.

Les puedo decir que lo mejor que anduvo fue Windows XP, Xubuntu fue lo peor, pasando por varios desktop lo mejor fue LXDE, Hoy mismo probe con OpenGeu(enlightement + gtk) y debo decir que si bien anda mejor, no es lo que esperaba.

Como la PC esta no tiene lectora, le saqué/co el disco rigido y lo pongo en la mia, ahi anda todo mas rapido e instalo en 15min. Obviamente una vez que termina la instalacion en el disco en mi pc, anda genial, mucha velocidad, pero cuando pongo el disco en la otra, ... (n)

En fin, estaba pensando si influia ese cambio de hardware, quizas el ubuntu le asignaba un kernel no optimizado para la otra computadora, lo que hacia que ensima, ande mas lento.

---

### Post by guisheca on 2008-10-18
Yo creo que obviamente influye, pensá que ubuntu instaló todo para tu pc, placa de video, sonido, monitor, teclado, mouse, etc. Al pasar el disco a otra pc ya no es lo mismo, no se si te detecta los cambios de hardware.
El otro día le instalé xubuntu al dinosaurio de mi novia, y solo traje su gabinete. Le instalé todo y cuando se lo llevé no me reconocía el monitor, por lo tanto no me levantaba las Xs. En ese caso una papa porque con un reconfigure xserver-xorg safé de 10, pero ya si es TODO el hardware... no se che, para mi no tiene porqué levantar siquiera.
Probá instalar todo desde la pc de ella, por mas que tarde 30 años, creo que es lo mejor. Hay métodos para instalar desde un pen drive, es cuestión de buscar.
Saludos.

---

### Post by vampichoke on 2008-10-18
este domingo regalale una compu a tu vieja y quedas como un rey. (obvio con hardy o intrepid ^^)

---

### Post by victor_nesta on 2008-10-18
> **vampichoke said:**
> este domingo regalale una compu a tu vieja y quedas como un rey. (obvio con hardy o intrepid ^^)
Y si...  jeje

---

### Post by faktorqm on 2008-10-20
> **guisheca said:**
> Yo creo que obviamente influye, pensá que ubuntu instaló todo para tu pc, placa de video, sonido, monitor, teclado, mouse, etc. Al pasar el disco a otra pc ya no es lo mismo, no se si te detecta los cambios de hardware.
El otro día le instalé xubuntu al dinosaurio de mi novia, y solo traje su gabinete. Le instalé todo y cuando se lo llevé no me reconocía el monitor, por lo tanto no me levantaba las Xs. En ese caso una papa porque con un reconfigure xserver-xorg safé de 10, pero ya si es TODO el hardware... no se che, para mi no tiene porqué levantar siquiera.
Probá instalar todo desde la pc de ella, por mas que tarde 30 años, creo que es lo mejor. Hay métodos para instalar desde un pen drive, es cuestión de buscar.
Saludos.

Ocurre exactamente lo contrario a lo que afirma guisheca. Particularmente en ubuntu, (no lo generalizo a otros gnu/linux's) cuando cambias de hardware no pasa nada mas que alguna que otra reconfiguracion (en el 90% de los casos del servidor X) y todo sigue andando bien.
Incluso Hei Ku cambio de mother y todo siguio andando perfecto. Creo que lo que probo y si no se lo banco el kernel es pasar de un micro de 64 a 32 o al reves y eso no arranco. (live cd y reconfigurar el kernel... jjijij)

Para esa pc pol, lo unico que iria bien creo es Elive GEM. Sino va eso...

---

### Post by guisheca on 2008-10-20
> **faktorqm said:**
> Ocurre exactamente lo contrario a lo que afirma guisheca. Particularmente en ubuntu, (no lo generalizo a otros gnu/linux's) cuando cambias de hardware no pasa nada mas que alguna que otra reconfiguracion (en el 90% de los casos del servidor X) y todo sigue andando bien.
Incluso Hei Ku cambio de mother y todo siguio andando perfecto. Creo que lo que probo y si no se lo banco el kernel es pasar de un micro de 64 a 32 o al reves y eso no arranco. (live cd y reconfigurar el kernel... jjijij)

Para esa pc pol, lo unico que iria bien creo es Elive GEM. Sino va eso...

DE VERDAD!!??, bueno por un lado perdón por dar info erronea, menos mal que puse que eso era lo que CREIA, porque si no quedaba como un perejil :mrgreen:. Pero por otro me llena de satisfacción que nuestro sistema haga eso (además de todo lo bueno que ya hace).
Cada día me congratulo mas de ser usuario de GNU/Linux!!!.
Saludos.

---

### Post by pol666 on 2008-10-20
Osea andar anda pero lento

Y que onda con el kernel. 8.04 le asigno en mi pc un i686  (es un Dual Core intel ) y la  otra una 750Mhz amd

---

### Post by chalito on 2008-10-20
No deberia joder eso, las dos maquinas que describis funcionan como i686 por decirlo de alguna manera.. la unica diferencia es que en la que es dual core podes hacer de cuenta que tenes dos micros y hacer smp, pero eso es transparente para el user y el sistema lo maneja solito.

La ram que tenes es poca, a lo mejor el sistema se la pasa trasheando? en eso puede influir la cantidad de swap que tenes, y los settings del disco en el que esta. Te fijaste haciendo un hdparm al disco rigido de esa maquina a ver como esta seteado? asegurate que tenga el dma activado y que use 32bit I/O si está soportado.

---

### Post by Hei Ku on 2008-10-20
Yo cambié el mother (MSI a ASUS), micro (AMD64 a AMD64 x4), placa de video y memoria. Con lo unico que tuve que hacer cosas fue con la placa de video, y la placa de red que tuve que reconfigurar el firewall.
El resto, levantó todo en mi Hardy que lo vengo actualizando desde la 6.10.
Eso es porque los drivers se levantan en general en modo dinámico, asi q reconoce q levantar al inicio.

---

