---
title: "Placa WIFI en Bangho M72S"
date: 2009-06-20
forum: Hardware
---

### Post by javierlinux1 on 2009-06-20
Publiqué esto en la lista, pero insisto por acá ya que necesito resolverlo con la mayor celeridad posible. Pido disculpas a quienes lo lean duplicado y agradezco a quin me pueda dar una mano:

Buenas tardes a todos, necesito configurar la placa wifi de una Banghó
M72S  y a pesar de haber googleado un rato, no doy pie con bola...

El SO detecta la placa como wlan1, si le doy iwconfig desde consola,
me devulve los datos, pero no se conecta a la red. Es decir hace el
proceso de conexión y me pide la clave, la coloco, sigue, diciendo que
se est{a conectanto y que está buscando la direccion de la red y pasan
unos segundos y devuelve que no se conectó.

Si alguien me puede dar una mano de que puntos chequear, les agradezco

Javier

---

### Post by guillermolisi on 2009-06-20
> **javierlinux1 said:**
> Publiqué esto en la lista, pero insisto por acá ya que necesito resolverlo con la mayor celeridad posible. Pido disculpas a quienes lo lean duplicado y agradezco a quin me pueda dar una mano:

Buenas tardes a todos, necesito configurar la placa wifi de una Banghó
M72S  y a pesar de haber googleado un rato, no doy pie con bola...

El SO detecta la placa como wlan1, si le doy iwconfig desde consola,
me devulve los datos, pero no se conecta a la red. Es decir hace el
proceso de conexión y me pide la clave, la coloco, sigue, diciendo que
se est{a conectanto y que está buscando la direccion de la red y pasan
unos segundos y devuelve que no se conectó.

Si alguien me puede dar una mano de que puntos chequear, les agradezco

Javier
Esa maquina tiene chipset SIS, cierto ?
Podrias enviar la salida de lspci ?

Probaste en una red sin seguridad a ver que pasa ?

Edit: Acabo de leer el thread en la lista y me quedo una duda. Usas Kubuntu o Ubuntu en la Bangho ?
Si usas Kubuntu ya te digo que su Network Manager no funciona bien. Una alternativa seria Wicd que a muchos les ha resultado mas funcional.

---

### Post by javierlinux1 on 2009-06-20
[QUOTE=guillermolisi;7489954]Esa maquina tiene chipset SIS, cierto ?

Cierto

Podrias enviar la salida de lspci ?

Acá va:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
00:09.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
00:09.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Probaste en una red sin seguridad a ver que pasa ?

No, no tengo ninguna a mano, estoy en la casa de la persona y tiene esa red, no quiero tocar nada, porque viste como es esto, tocas algo que anda y no vuelve a andar más!!!

Espero que me puedan ayudar con eso que pase.

Gracias

Edit: Acabo de leer el thread en la lista y me quedo una duda. Usas Kubuntu o Ubuntu en la Bangho ?

estoy usando kubuntu, pero tengo los dos, puedo entrar por gnome igual, si es mas facil y una vez que este configurado puedo volver a KDE y que siga andando me da lo mismo

gracias de nuevo

---

### Post by guillermolisi on 2009-06-20
> **javierlinux1 said:**
> [quote=guillermolisi;7489954]Esa maquina tiene chipset SIS, cierto ?

Cierto

Podrias enviar la salida de lspci ?

Acá va:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
00:09.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
00:09.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Probaste en una red sin seguridad a ver que pasa ?

No, no tengo ninguna a mano, estoy en la casa de la persona y tiene esa red, no quiero tocar nada, porque viste como es esto, tocas algo que anda y no vuelve a andar más!!!

Espero que me puedan ayudar con eso que pase.

Gracias

Edit: Acabo de leer el thread en la lista y me quedo una duda. Usas Kubuntu o Ubuntu en la Bangho ?

estoy usando kubuntu, pero tengo los dos, puedo entrar por gnome igual, si es mas facil y una vez que este configurado puedo volver a KDE y que siga andando me da lo mismo

gracias de nuevo
Javier

Me llama la atencion que no aparece ninguna interface WiFi en ese listado.
Aparece la de 1Gb que es cableada pero ninguna WiFi.

Estara encendida la antena ?

Fijate que tenes en una tecla de funcion el icono de antena WiFi que se activa presionandolo con la tecla Fn + la tecla de funcion con ese icono.
Una vez la enciende y a la siguiente la apaga. Para guiarte se debe encender un led en el frente de la maquina.

Edit: Acabo de leer el thread en la lista ... que caro que te va a salir esto ! :D

---

### Post by faktorqm on 2009-06-21
a parte de mirar lo que te dijo guille, postea "lsusb" tambien, a veces la wi-fi puentea internamente con el usb. otra cosa que te podrias fijar tmabien, es si esta activada en el bios. salu2!

---

