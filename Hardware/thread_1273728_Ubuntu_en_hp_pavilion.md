---
title: "Ubuntu en hp pavilion"
date: 2009-09-23
forum: Hardware
---

### Post by Espirin on 2009-09-23
Hola, soy nuevo en el mundo de linux y hace poco instale ubuntu 9.04 en hp pavilion 2422la, el tema es que no detecta mi red wifi que proviene de un router zyxel de los que da telefonica de argentina, pero si reconoce otras redes que proviene de otras marcas de routers como linksys, tampoco me deja poner mi tarjeta broadcom bcm 4311 en modo monitor, si alguien me puede dar una mano les agradeceria.

---

### Post by pablo.s on 2009-09-23
Con respecto a la red WiFi
que no detecta, constatá en
la configuración del router
que la el ESSID y/o BSSID
no estén ocultos (digamos
que el modo de difusión no 
esté desactivado, eso es)

---

### Post by Espirin on 2009-09-24
Gracias pablo.s por responder, el tema es que con win xp me la reconoce, la ESSID no esta oculta, lo que probe fue otros drivers para esta tarjeta Broadcom, me detecto mi red pero no me deja conectarme, ahora estoy conectado por medio de Win XP, y me gustaria hacerlo desde ubuntu asi que cualquier ayuda biene bien

---

### Post by Hei Ku on 2009-09-24
Habilitaste los repositorios restringidos e instalaste el driver para esta placa?

Es una placa PCI o USB?

---

### Post by Espirin on 2009-09-24
Hola Hei Ku, mira es la que trae de fabrica la notebook, ahora tegno instalado los drivers que trae el cd ubuntu para esta placa, con respecto a los repositorios restringidos diculpa mi ignorancia pero no se que es. El tema es que desde otras redes wifi que engancho puedo conectarme pero de la que emite mi router no, ni si quiera la veo, cosa q con xp no pasa. gracias por responder

---

### Post by Hei Ku on 2009-09-24
Poné en una terminal:

```
lspci
```

y

```
iwconfig
```

Y copiá el resultado de los dos y postealos acá.

---

### Post by Espirin on 2009-09-24
Hola aca dejo lo que me pediste


mauricio@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)



mauricio@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

Espero que me puedan dar una mano, si no igual muy agradecido por contestar.

---

### Post by Hei Ku on 2009-09-24
Andá a Synaptic, gestionar repositorios, y fijate que tengas habilitados los repositorios restringidos.

---

### Post by Espirin on 2009-09-24
Kei ku, entré donde me dijiste y los repositorios restringidos, estan habilitados, la verdad es que no se que puede pasar, tampoco puedo ponerla en modo monitor, desde ya muchas gracias....

---

### Post by Hei Ku on 2009-09-24
En el menú de aplicaciones del sistema debería aparecerte algo como Controladores de Hardware, donde podes ver si el driver de la placa esta habilitado, aunque supongo que sí.

Que estas usando para conectarte por wifi? El Networkmanager?

---

### Post by Espirin on 2009-09-24
Como bien dijiste, el controlador de hadware esta habilitado, si utilizo el [I]network manager que es el que trae por defecto ubuntu 9.04.
Creo que lo mejor va a ser cambiar el router.
[/I]

---

### Post by sergiom99 on 2009-09-24
> **Espirin said:**
> Como bien dijiste, el controlador de hadware esta habilitado, si utilizo el [I]network manager que es el que trae por defecto ubuntu 9.04.
Creo que lo mejor va a ser cambiar el router.
[/I]
Yo empezaria cambiando el Network Manager por Wicd
```
sudo apt-get install wicd
```

Avisa como te fue.
Saludos- Sergio

---

### Post by Espirin on 2009-09-24
Disculpa Sergio, tengo que desinstalar primero el networ manager, o no hay drama, gracias por responder y por ayudar a gente principiante

---

### Post by luks911 on 2009-09-24
> **Espirin said:**
> Disculpa Sergio, tengo que desinstalar primero el networ manager, o no hay drama, gracias por responder y por ayudar a gente principiante

No hace falta. Ejectá el comando tal cual te lo pasó Sergio
```
sudo apt-get install wicd
```
que el sistema sólo se encarga de desinstalar Network-manager y reemplazarlo por Wicd.

---

### Post by Espirin on 2009-09-24
Sergio esto es lo que me sale

mauricio@ubuntu:~$ sudo apt-get install wicd
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete wicd
mauricio@ubuntu:~$ 

Lo estoy cargando desde los repositores, te aviso si funciona gracias

---

### Post by sergiom99 on 2009-09-24
Aclaro, por las dudas, pero para instalarlo con apt-get tenes que estar conectado a internet. Asi que si el wifi no anda, conectala con cable.

---

### Post by Espirin on 2009-09-25
Pablo mira puse, el wicd pero sigo sin poder ver la red wifi, me sigue encontrando las misma que con el otro, pero no encuentra la mia, que mas se puede hacer, gracias de antemano

---

### Post by sergiom99 on 2009-09-25
Fijate este thread [1] Mismo modelo de placa y todo.
No te hace falta instalar nada a mano, solo tenerlo actualizado al ubuntu y activar los drivers

[1] [http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)

---

### Post by Hei Ku on 2009-09-25
> **sergiom99 said:**
> Fijate este thread [1] Mismo modelo de placa y todo.
No te hace falta instalar nada a mano, solo tenerlo actualizado al ubuntu y activar los drivers

[1] [http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)

Ya tiene los drivers activados, asi que no es eso.


Podes tirarnos mas datos sobre como es la red a la que te queres conectar?

---

### Post by Espirin on 2009-09-25
Si, la el router que emite la señal es un zyxel P-660HW, de los que da Telefonica de Argentina, la clave es wep, no se que mas puedo decirte, mediante cable funciona correctamente, lei por ahi que con el aircrack pero tampoco me deja ponerla en modo monitor. mira hace mucho cuando tenia la version 8.04 tampoco podia instale otro driver pero no recuerdo cual, con ese driver aunque sea podia detectarla pero no podia conectarme, ponia la clave y nada. Desde ya gracias

---

