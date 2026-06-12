---
title: "Ubuntu 8.04 en dell inspiron 1525"
date: 2008-05-13
forum: Hardware
---

### Post by cere.nofx on 2008-05-13
Hola gente que tal, me alegro de que exista este foro.. Hace unos 20 dias pedi una Dell inspiron 1525 la cual viene con Windows Vista Home Premium, a la semana de comprarla salió el mismo equipo pero con ubuntu, asi que ya era tarde para modificar el pedido.. es mi primera vez con una laptop, y a la vez la primera vez que me animo a instalar y usar el Ubuntu pero no se como instalarlo, si alguien por favor podria explicarme facilmente como hacer para formatear la pc e instalar el ubuntu 8.04 porq no quiero el vista ni un poco ni quiero que quede en la pc.. y realmente no se nada de programacion ni nada por el estilo pero quiero el ubuntu 8.04 que ya bajé- Muchisimas graciaaaaaaas si alguien pudiera ayudarme seria genial, y seria genial tambien difundir el ubuntu y que mucha mas gente como yo, sin conocimientos de programacion pueda acceder a este software..

---

### Post by patagonik on 2008-05-13
Hola!

Aqui tienes un [tutorial]("http://libera2.wordpress.com/2006/06/07/instalacion-de-ubuntu/") con imagenes y todo eso, y si no abajo describo un poco más corto

1. Cuando tengas el portatil arrancalo con el [Live CD]("http://www.ubuntu.com/getubuntu/download") de ubuntu. Normalmente la compu va a arrancar del disco antes que del hard drive, asi que te saldrá un panel proponiendote varias opciones: tendrás que elegir entrar en Ubuntu, o usar Live CD o algo asi. 
2. El sistema cargará desde el CD y entrarás en el escritorio GNOME, y entre otros iconos del escritorio estará "Instalar Ubuntu" (hasta aqui no ha ocurrido nada, no has tocado tu instalacion de Vista). 
3. Cliquea sobre ese icono y entrarás en un ayudante que te guiará para configurar teclado, idioma, hora, codigos, etc... 
4. Llegado un punto te preguntará si quieres que Ubuntu configure los discos para la instalación o si quieres hacerlo manualmente... elige esta segunda opcion. Podrás ver la configuración de discos duros y de ahi decidir dónde lo quieres instalar: normalmente tendrás un disco duro y puede que varias particiones. Ahora tienes que decidir si dejar tu portatil con Dual Boot (al iniciar el ordenador podrás elegir entre Vista y Linux) o eliminar la instalación de Vista y dejar solamente Ubuntu. No te sabría explicar ahora los pasos exactos a tomar, pero recuerdo que era bastante intuitivo la vez que lo hice.
5. Confirma tu elección y miralo trabajar hasta que se instale.
6. Reinicia el portatil habiendo extraido el CD y listo.

Una cosa que te aconsejo que hagas es antes que nada: entrar en Vista, actualizar el sistema y hacer un RecoveryCD, que podrias llegar a necesitar en el futuro (no se cuanto has usado Linux) como CD de instalación. 
Sobre todo lee atentamente todo lo que aparezca durante la instalacion de Ubuntu y si tienes la opcion de consultar la ayuda seguro que resolveras tus dudas.

Cualquier cosa postea por aqui que seguro alguien te ayuda. Suerte!

---

### Post by Simbiosys on 2008-05-23
Buenas, tengo justamente la misma portatil... pero no logro hacer funcionar la placa de red wireless... leí por ahí algunas guias y comandos que dicho sea de paso nisiquiera se que efecto tendrían en mi sistema. Me da un poco de miedo tipear y apretar enter porque sí... les cuento que si escribo "lshw" el resultado respecto a la placa es:

  
           *-network UNCLAIMED
                description: Network controller
                product: BCM4310 USB Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0

La verdad es que hasta donde entiendo, la placa la detecta. Dice network UNCLAIMED... ¿Esto que significa? Si abro la utilidad de red del ubuntu, la conexión inalámbrica no aparece.

Leí por todos lados que por defecto el ubuntu reconocía la placa, pero no sucedió esto en mi caso.

Saludos. y mil gracias de antemano.

---

### Post by Simbiosys on 2008-05-23
Gente, despues de unas buenas horas de lucha... logré encontrar la solución al problema... les dejo un link en donde está muy bien explicado.
[http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html](http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html)

Saludos.

---

