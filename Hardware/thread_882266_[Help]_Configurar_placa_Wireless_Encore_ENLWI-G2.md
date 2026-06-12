---
title: "[Help] Configurar placa Wireless: Encore ENLWI-G2"
date: 2008-08-06
forum: Hardware
---

### Post by majatu on 2008-08-06
Muy buenas gente, como dice el titulo, necesito ayuda para hacer funcionar una placa wireless Encore ENLWI-G2 en Ubuntu Hardy.

Intente con algunos tutoriales pero me mezclan drivers de windows y que haga andar con Wine la utilidad que trae la placa.

Yo necesito repos para Ubuntu o de ultima q utilitario instalar para hacerla funcionar.

Espero puedan ayudarme, muchas gracias de antemano! :)

---

### Post by Hei Ku on 2008-08-06
En muchos casos las placas wireless funcionan mejor con ndiswrapper. Si bien es una solucion de compromiso, andan bien para el uso normal que uno le da a la placa. No permiten cosas mas avanzadas como el sniffing de paquetes, pero eso es algo fuera del uso normal.

Para poder ayudarte necesitariamos saber qué chipset tiene.
Posteá el resultado del comando lspci.

---

### Post by majatu on 2008-08-07
> **Hei Ku said:**
> En muchos casos las placas wireless funcionan mejor con ndiswrapper. Si bien es una solucion de compromiso, andan bien para el uso normal que uno le da a la placa. No permiten cosas mas avanzadas como el sniffing de paquetes, pero eso es algo fuera del uso normal.

Para poder ayudarte necesitariamos saber qué chipset tiene.
Posteá el resultado del comando lspci.

[B]El chipset de la placa es un Realtek RTL-8185 IEEE 802.1

Igual dejo la salida del comando lspci:
[/B]
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
00:0f.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
00:10.0 Class ffff: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev ff)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)



***** EDIT *****

Ya pude hacerla funcionar instalando los drivers de Windows XP mediante ndiswrapper, lo demas fue configurar el acceso al router, asi que ya esta solucionado.

Muchas gracias! ;)

---

### Post by kuarahy on 2009-10-05
Hola Majatu. ¿Cual driver seleccionaste para lograr la instalacion? Porque he seleccionado de XP y creo que de 2000 y no me aceptó, me dio un mensaje de error. 

Me podrias indicar tambien los pasos de configuracion del router?

---

### Post by guillermolisi on 2009-10-05
> **kuarahy said:**
> Hola Majatu. ¿Cual driver seleccionaste para lograr la instalacion? Porque he seleccionado de XP y creo que de 2000 y no me aceptó, me dio un mensaje de error. 

Me podrias indicar tambien los pasos de configuracion del router?
Tene presente que este thread data de algo mas de un año atras y es posible que los kernels actuales incluyan drivers como los que estas necesitando con lo cual no haria falta usar ndiswrapper.

Para tener certeza del chipset que esta usando esa placa nada mejor que ver la salida del comando "lspci" (sin las comillas).

---

