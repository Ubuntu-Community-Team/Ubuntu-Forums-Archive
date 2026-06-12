---
title: "Xubuntu+Encore ENLWI-G2 se cuelga al inicio"
date: 2009-06-06
forum: Hardware
---

### Post by marcosconio on 2009-06-06
Buenos días foro.

Les cuento mi situación. 

Estoy intentando dejar funcional una máquina que tenía inactiva(Athlon XP 2600+, asrock K7S41GX, 512MB). Le acabo de instalar xubuntu 9.04 desde un alternate perfectamente y logré loguearme a la perfección.

Luego, le coloqué una placa PCI Wireless Encore ENLWI-G2, bootea bien, pero al momento de cargar el gdm, se cuelga completamente, dejando de responder la máquina. Ni siquiera me deja acceder a la consola.

Si booteo en recovery mode, logro iniciar bien, logrando llegar al cli. Desde acá puedo sacarles alguna información extra para que me ayuden.

Espero que alguien pueda ayudarme.

Saludos, Marcos

---

### Post by Hei Ku on 2009-06-06
seria bueno que hicieras lspci y postees esa informacion.

Esa placa es una sintonizadora o una Wifi?

---

### Post by marcosconio on 2009-06-06
> **Hei Ku said:**
> seria bueno que hicieras lspci y postees esa informacion.

Esa placa es una sintonizadora o una Wifi?

Esa placa es una wifi.

Este es el resultado de ejecutar lspci:
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

Por lo que veo, si la reconoce:
```

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```

Saludos, Marcos

---

### Post by marcosconio on 2009-06-06
Si entro desde el recovery menu, pero en vez de la entrada "root", lo hago desde "netroot", que me da un "shell promt with networking", me da el siguiente mensaje:
```

wmaster0: unknown hardware address type 801
```
y se vuelve a colgar.

Otra cosa que hice:
siguiendo la guia [http://www.vicente-navarro.com/blog/2009/03/01/configurar-wep-y-wpa-en-linea-de-comandos-y-en-el-arranque-en-debian-y-ubuntu/]("http://www.vicente-navarro.com/blog/2009/03/01/configurar-wep-y-wpa-en-linea-de-comandos-y-en-el-arranque-en-debian-y-ubuntu/"), 
hice(linksys es el essid de la red a la que me puedo conectar) : 
```

$ iwconfig wlan0 essid linksys
$ ifconfig wlan0 up

```
y al momento de levantarla, muere :(

Saludos, Marcos

---

### Post by Hei Ku on 2009-06-06
podes fijarte en otra pc que esa placa ande bien? me suena a que debe tener algun problema y por eso te cuelga la pc.

---

### Post by marcosconio on 2009-06-06
> **Hei Ku said:**
> podes fijarte en otra pc que esa placa ande bien? me suena a que debe tener algun problema y por eso te cuelga la pc.
No che. A pura notebook por aca.
Me la compre ayer a la placa. Seria una lastima que no anduviera.
Me instalo un windor y veo si anda con el driver que trae.

Gracias,
Saludos, Marcos

---

### Post by marcosconio on 2009-06-06
Buena? noticia. Estoy en window$, y la placa anda perfectamente.
Estuve leyendo por ahi que la placa ha sido instalada satisfactoriamente en xubuntu 7.10 con ndiswrapper. Tal vez sea hora de quemarlo en el regrabable e instalar esa version.
Quería algo mas nuevito, pero si no se puede... prefiero eso a este xp.

Gracias,
Saludos, Marcos

---

### Post by pablo.s on 2009-06-06
Ndiswrapper no es exclusivo
de Xubuntu, ni de Ubuntu 7.10.
En todo caso esta como paquete
en los repositorios, fijate de
seguir las indicaciones que
encontraste.

El cuelgue que mencionas me
pasaba a mi hace un par de años
con una Ralink RT2561. Pero ya
no lo hace mas, el driver esta
integrado en el kernel, ahora.
¿Que version de Ubuntu tenes?

---

### Post by Hei Ku on 2009-06-06
Una alternativa es probar con ndiswrapper, que es basicamente utilizar los drivers de windows, bajo linux.

[http://www.ubuntu-es.org/index.php?q=node/81741](http://www.ubuntu-es.org/index.php?q=node/81741)

---

### Post by marcosconio on 2009-06-06
> **pablo.s said:**
> Ndiswrapper no es exclusivo
de Xubuntu, ni de Ubuntu 7.10.
En todo caso esta como paquete
en los repositorios, fijate de
seguir las indicaciones que
encontraste.

El cuelgue que mencionas me
pasaba a mi hace un par de años
con una Ralink RT2561. Pero ya
no lo hace mas, el driver esta
integrado en el kernel, ahora.
¿Que version de Ubuntu tenes?

> 
Una alternativa es probar con ndiswrapper, que es basicamente utilizar los drivers de windows, bajo linux.

[http://www.ubuntu-es.org/index.php?q=node/81741](http://www.ubuntu-es.org/index.php?q=node/81741)

Ya he instalado otra placa con ndiswrapper en el pasado.

En esta máquina tenía instalado xubuntu 7.10, le instalé arriba el xubuntu 9.04. Al parecer este último tiene algún problema con el driver de la placa, y el más viejo no, porque el más viejo no se me colgaba al intentar levantar la interfaz WLAN0. Eso debe haber sido porque directamente no tenía registro de ese driver ¿? No se, me parece que estoy delirando :P.
El 9.04 arranca bien sin los servicios de red. Al intentar levantar la interfaz de la placa, chan, se muere.

La solución de ndiswrapper la había pensado. Pero no sé, si instalo el driver con ndiswrapper, ¿no me va a crear conflictos con el driver que ya trae el xubuntu?

Saludos, Marcos

---

### Post by pablo.s on 2009-06-07
Probalo. Perder nada,
ganar mucho.

---

### Post by marcosconio on 2009-06-07
> **pablo.s said:**
> Probalo. Perder nada,
ganar mucho.

ja, so true.
Mañana pruebo y cuento.

Gracias por el consejo.
Saludos, Marcos

---

### Post by Hei Ku on 2009-06-07
Fijate en el link que te pase, que lo primero que hacen es poner en blacklist el driver del kernel. Justamente para evitar conflictos con lel ndiswrapper.

---

