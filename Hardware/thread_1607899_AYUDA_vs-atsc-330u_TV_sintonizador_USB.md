---
title: "AYUDA vs-atsc-330u TV sintonizador USB"
date: 2010-10-28
forum: Hardware
---

### Post by chirijose on 2010-10-28
tengo este sintonizador usb tv vs-atsc-330u y deseo saber como instalarlo en ubuntu o en fedora no quiero utilizar windows 
gracias :)
AYUDENMEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEE

---

### Post by Wiredfixer on 2010-10-28
Que has intentado hacer?

Ya buscaste en los foros?

Porque no pones mas especificaciones de la PC?

Que te dice el comando de "lsusb"?

Cual es tu sistema Ubuntu?

Y si bien lees, es un foro de UBUNTU, no de fedora...

---

### Post by chirijose on 2010-10-28
-Pues pense q instalando algun programa estandar pero no encuentro el programa
-Busque pero no encontre de este modelo

PC
-dp35dp - 4 gigas ram - Ubuntu de 64bits - 

#lsusb
-despues de 1 hora aun no imprime informacion

dije fedora p1 tambien tengo el fedora y tambien el ubuntu
por lo general uso ubuntu mas facil de encontrar programas
pero por siaca tengo fedora tambien
cualquiera me ayuda

---

### Post by Wiredfixer on 2010-10-29
Bueno, pues segun lo que encontre de tu USB:

[http://linuxtv.org/wiki/index.php/Em28xx_devices](http://linuxtv.org/wiki/index.php/Em28xx_devices)

El chipset que usa es un EM 2880, de hecho, precisamente para eso es el comando de lsusb..

intenta el lsusb y checa la salida.. luego inserta el usb y otra vez pon el comando en la terminal de lsusb, debe haber diferencia.

basicamente, necesitas ver si el Modulo del Chipset que requieres esta cargado en tu Kernel, de no estarlo, lo puedes hacer como en la pagina que te puse.

Ya insertado el USB, solo bastaria con Iniciar tu aplicacion preferida de TV.

Funciona en Windows?

---

### Post by cmonsalvo on 2012-09-23
Hola, ya tengo como 2 semanas intentando buscar la forma de ver la TV Digital ATSC en mi Ubuntu 12.04, pero no he tenido éxito. En Windows 7, solo conecto la tarjeta USB, abro Windows Media Center, selecciono México y en un par de minutos me detecta todos los canales de Alta Definición de la ciudad, e incluso los puedo grabar. Pero por mi educación y cuestiones éticas he decidido utilizar Ubuntu desde hace más de 1 año, pero lo único no he podido conseguir es que pueda ver TV digital en el sistema. 

Al parecer si detecta muy bien la tarjeta, ya que con Me-TV puedo ver el S-Component(Video auxiliar -amarillo, blanco y rojo) cuando le conecto Dish, aunque no se escucha.

De tal forma que mi problema es creo, al configurar la tarjeta y escanear los canales de México. Alguien podría ayudarme con este problema?, de antemano muchas gracias.

Coloco TODOS los datos concernientes a la tarjeta, SO, y todo.

**Ubicación:**
Ciudad de México, México. (ATSC)

**Tarjeta sintonizadora:**
Kworld PlusTV HD Hybrid Stick (ATSC 330U)
Es una tarjeta híbrida que puede sintonizar TV Digital y análoga.

Componentes:
Xceive XC3028 (tuner & analog demod)
TI TVP5150 (A/V decoder)
Samsung S5H1409 (digital demod)
Empia EM2883 (USB bridge)
Identification
Output of lsusb -v reveals a subsystem ID of: eb1a:a316

Ubicación en card List:  57 -> Kworld PlusTV HD Hybrid 330              (em2883)        [eb1a:a316]
[http://www.kernel.org/doc/Documentation/video4linux/CARDLIST.em28xx](http://www.kernel.org/doc/Documentation/video4linux/CARDLIST.em28xx)

Tuner List: tuner=71 - Xceive xc2028/xc3028 tuner
[http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.tuner;filenode=-1;style=raw](http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.tuner;filenode=-1;style=raw)

Página del vendedor:
[http://mx.kworld-global.com/main/prod_in.aspx?mnuid=1424&modid=18&fcid=14&pcid=255&ifid=145&prodid=259&flag=1](http://mx.kworld-global.com/main/prod_in.aspx?mnuid=1424&modid=18&fcid=14&pcid=255&ifid=145&prodid=259&flag=1)

Referecia de video for Linux:
[http://linuxtv.org/wiki/index.php/KWorld_ATSC_330U](http://linuxtv.org/wiki/index.php/KWorld_ATSC_330U)

**Como la detecta MI sistema**
lsusb:
Bus 002 Device 004: ID eb1a:a316 eMPIA Technology, Inc.

Me-TV (Asistente de barrido), Kaffeine:
Samsung S5H1409 QAM/8VSB Fronted

**Sistema:**
Ubuntu 12.04 LTS 64 bits.
Acer Aspire 6920
CPU: Intel® Core™2 Duo CPU T7500 @ 2.20GHz × 2
Gráficos: Intel® 965GM
Memoria RAM: 2 GB
Disco Duro: 250 GB

---

