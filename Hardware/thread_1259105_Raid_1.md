---
title: "Raid 1"
date: 2009-09-05
forum: Hardware
---

### Post by panchoarq on 2009-09-05
Hola,
tengo un servidor Dell Powerdwge T-100 con 2 discos y un atarjeta controladora Raid. Al instalar Ubuntu no reconoce los discos ni el Raid y no aparecen en el Equipo.
¿alguna idea de como solucionar esto?
 
Muchas Gracias

---

### Post by gmunioz on 2009-09-05
Hola pan....:

Aqui un how-to:

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

---

### Post by kamus on 2009-09-06
Si tu controladora no esta soportada a nivel de hardware siempre esta la oportunidad de hacerlo por software ;)

---

### Post by panchoarq on 2009-09-07
Al instalar Ubuntu, me aparece solo un disco de 250 GB, no aparece el segundo instalado. Disculpen la ignorancia pero no deberían aparecer los dos discos?. Al iniciar Ubuntu, en otras ocasiones en otros pc me mostraba los distintos discos presentes pero ahora solo me aparece el cd-rom y "Sistema de archivos", ningún disco. Me podrían orientar sobre cpmo arreglar este tema para luego configurar el Raid 1. Mi controladora es una SAS6iR de LSi. En la página de Dell,el fabricante del servidor y de LSi, hay dirvers para Linux Red Hat Enterprise Linux 4, 5 y SuSE Linux Enterprise Server 9 y 10. ¿estos drivers me sirven? Si es así cuál sería la manera de habilitar los discos y que Ubuntu los reconozca y por otro lado como le instalo el driver, si es que sirve, para poder habilitar el Raid 1.

---

### Post by kamus on 2009-09-07
En el wiki [https://help.ubuntu.com/community/FakeRaidHowto#RAID-1](https://help.ubuntu.com/community/FakeRaidHowto#RAID-1) esta todo documento. De todas maneras lo mas sencillo si recien instalaste el sistema es volver a instalar y desde el instalador configurar el raid (almenos deberia detectarte ambos discos).

Saludos

---

### Post by centurix on 2009-09-08
existe driver para la tarjeta raid en RH. Creo que deberías bajar dicho driver de la página de Dell y preparar el diskette del driver para configurar la tarjeta en la instalación.

Otra opción es realizar una instalación mínima y configurar el espacio del raid una vez instalado el driver (utiliza alien para convertir el rpm a deb).

Un saludo

---

