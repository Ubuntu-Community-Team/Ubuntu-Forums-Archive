---
title: "Wifi de Compaq Presario V2000"
date: 2009-09-13
forum: Hardware
---

### Post by Pulgatita on 2009-09-13
Tengo un problema para conectar mi computador Compaq Presario V2000. Intenté activar los controladores restringidos pero no aparece ninguno. (Es relevante que diga que instalé Windows y Ubuntu en el disco, con sus respectivas particiones?) (Además la primera vez que instalé ambos sistemas operativos lo hice en el orden incorrecto, instalé ubuntu primero y despues windows, en ese caso logré hacer funcionar la conexión WIFI, activando los controladores restringidos), ahora buscando información en los foros encontré que se podía hacer mediante ndiswrapper, y debo tener los drivers de mi tarjeta de red y cabextract, tengo todo eso pero cuando intento descomprimir los drivers en la terminal con el cabextract me sale:

wirelesskeyview.exe: no such file or directory
all done, errors in processing 1 file (s)

Podría alguien ayudarme?

---

### Post by Hei Ku on 2009-09-13
Por donde empezar, no?

Primero, te colgaste de un tema de wifi, pero que probablemente no sea el mismo modelo de tu placa, asi que te conviene empezar un tema nueva. Hecho.

Segundo, si antes te anduvo activando los repositorios restringidos, por que no lo hiciste de vuelta asi? 

Usar ndiswrapper esta totalmente desaconsejado cuando existe una alternativa nativa de Linux.

Tercero, seria bueno saber q placa tenes, que hasta ahora no nos dijiste. Si es usb, pone lsusb en una terminal y postea el resultado. Si es interna, pone lspci en la terminal y postea el resultado. Ante la duda, postea los dos.

---

### Post by Pulgatita on 2009-09-13
Trate de activar los controladores restringido, no me aparece ninguno en la lista, no hay ninguno para activar
nose si seran los mismos que los repositorios restringidos
pase a la opcion de ndiswrapper porque no me queda otra forma para lograr la coneccion via wifi. 
La placa que tengo es interna y al poner lspci en el terminal me sale esto

bola@Bolazo:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

---

### Post by Hei Ku on 2009-09-13
Una vez que actives los repositorios restringidos, deberías ir a Controladores de Hardware y activar el paquete b43. Todo esto, suponiendo que estes usando Jaunty.

---

### Post by Pulgatita on 2009-09-13
Si, ya lo hice.... muchas gracias por tu ayuda. Te lo agradezco mucho.

---

### Post by Hei Ku on 2009-09-13
Entonces salio andando. Podes marcarlo como solved desde Thread tools?

---

### Post by benditoelqueviene on 2009-10-14
Lo hice como ustedes dice y me resulto!  Muchas gracias.  Me gustaria saber cual es la alternativa nativa a ndiswrapper.
Gracias

---

### Post by guillermolisi on 2009-10-14
> **benditoelqueviene said:**
> Lo hice como ustedes dice y me resulto!  Muchas gracias.  Me gustaria saber cual es la alternativa nativa a ndiswrapper.
Gracias
Si estas usando una version de kernel que incluya drivers Linux para Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller, entonces no deberias necesitar usar ndiswrapper.

---

### Post by Cbiz- on 2009-10-15
Hola a todos,
             tengo un tema similar con Ubuntu 9.10 (ya totalmente actualizado), no funciona el Wifi (Broadcom 4312); con el Mint 7 Gloria en otra partición funciona desde el momento de la instalación; me pueden ampliar el procedimiento con los restricted drivers?
Desde ya, muchas gracias.
Slds, Carlos

Notebook Lenovo G530

---

