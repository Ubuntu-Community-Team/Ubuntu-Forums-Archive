---
title: "Wifi en Dell XPS M1530"
date: 2010-01-07
forum: Hardware
---

### Post by Iced1 on 2010-01-07
Hola, he instalado Ubuntu 9.10 en mi notebook xps m1530, pero no me reconoce wifi, yo trato siempre de primero buscar soluciones y las encontre... tengo que activar el NOAPIC en el menu.lst del grub pero ahora en ubuntu 9.10 cambio a GRUB2 y no se como lo voy a hacer ahora, espero que me puedan ayudar, cualquier informacion que necesiten me la preguntan, saludos y gracias por escucharme.

---

### Post by Carlos C on 2010-01-07
Hola. Intenta ver el modelo exacto de tu tarjeta escribiendo el comando "lspci" en el terminal. Si no sabes identificarla copia acá todo lo que te salga.

Saludos.

---

### Post by moreback on 2010-01-07
Los Dell vienen con Broadcom por lo general, así que no debiera ser problema ayudarte. Pero sí es necesario saber qué modelo de tarjeta tienes y para eso la salida del comando **lspci** nos ayudará.

Saludos.

---

### Post by Iced1 on 2010-01-07
> **Carlos C said:**
> Hola. Intenta ver el modelo exacto de tu tarjeta escribiendo el comando "lspci" en el terminal. Si no sabes identificarla copia acá todo lo que te salga.

Saludos.

> **moreback said:**
> Los Dell vienen con Broadcom por lo general, así que no debiera ser problema ayudarte. Pero sí es necesario saber qué modelo de tarjeta tienes y para eso la salida del comando **lspci** nos ayudará.

Saludos.


Muchas gracias por tsus respuestas tan rapidas, ise lo que me han dicho y salio esto:

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

cabe resaltar que mi problema es que no salen las redes disponibles cercanas, sobre como configurarlo para que me de internet del router se como hacerlo, bueno gracias espero que me puedan ayudar.

---

### Post by CdK1 on 2010-01-07
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

Lee esto:

[http://barackman.wordpress.com/ubuntu-y-hp-pavilion-tx1232la-broadcom-corporation-bcm4312-80211abg-rev-02/](http://barackman.wordpress.com/ubuntu-y-hp-pavilion-tx1232la-broadcom-corporation-bcm4312-80211abg-rev-02/)

[http://linuxsix.blogspot.com/2009/01/instalar-broadcom-corporation-bcm4312.html](http://linuxsix.blogspot.com/2009/01/instalar-broadcom-corporation-bcm4312.html)

O puedes usar:


Caturra:/# apt-cache search bcm43
broadcom-sta-common - Common files for the Broadcom STA Wireless driver
broadcom-sta-source - Source for the Broadcom STA Wireless driver
b43-fwcutter - Herramienta para extraer el firmware de Broadcom 43xx
Caturra:/#

---

### Post by Iced1 on 2010-01-07
> **CdK1 said:**
> 0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

Lee esto:

[http://barackman.wordpress.com/ubuntu-y-hp-pavilion-tx1232la-broadcom-corporation-bcm4312-80211abg-rev-02/](http://barackman.wordpress.com/ubuntu-y-hp-pavilion-tx1232la-broadcom-corporation-bcm4312-80211abg-rev-02/)

[http://linuxsix.blogspot.com/2009/01/instalar-broadcom-corporation-bcm4312.html](http://linuxsix.blogspot.com/2009/01/instalar-broadcom-corporation-bcm4312.html)

O puedes usar:


Caturra:/# apt-cache search bcm43
broadcom-sta-common - Common files for the Broadcom STA Wireless driver
broadcom-sta-source - Source for the Broadcom STA Wireless driver
b43-fwcutter - Herramienta para extraer el firmware de Broadcom 43xx
Caturra:/#

ok gracias, copiare las paginas y reiniciare el notebook en ubuntu, otra cosa habia encontrado estas paginas con casos similares: [http://www.galmarino.com/wordpress/?p=31](http://www.galmarino.com/wordpress/?p=31) solo que el usa 7.10, y ahora en el 9.10 usa grub2 y es diferente, pero el que mas apunta al caso es este mira: [http://lists.us.dell.com/pipermail/linux-desktops/2009-November/003323.html](http://lists.us.dell.com/pipermail/linux-desktops/2009-November/003323.html) sobre todo esto: 

Si el sistema es un arranque dual como el mío, y GRUB es el
gestor de arranque, a continuación, las opciones de arranque se mostrará. Con la primera opción
resaltado, pulse E 'para editar la opción de arranque, y pase a la final de la
línea que comienza con "kernel", y escribe "noapic" después de "quiet splash". Entonces
pulse Ctrl-X para arrancar el sistema. Resultados - WiFi LED se ilumina, y el sistema de
conecta de forma inalámbrica. No es necesario volver a instalar los controladores, o vuelvo a ipw3945
de iwl3945. Network-Manager funciona correctamente, y "wicd" o de otros paquetes
no son necesarios, aunque se pueden utilizar (como por usuario de la elección personal).
(traducido) 

bueno lo ise, pero no entiendo donde exactamente tengo que colocar noapic, ahy dice despues de quiet splash lo ise pero no funciono asi que pienso que la traducion de google tiene un error, entonces no se donde, bueno gracias, ahora prosigo con lo que me mandaste =)

---

### Post by Carlos C on 2010-01-08
Antes de usar ndiswrapper o ponerte a compilar yo usaría el paquete b43-fwcutter. Si tu tarjeta está soportada creo que puede resultar más fácil:

[http://blockdeubuntu.blogspot.com/2008/08/conexin-wifi-en-ubuntu-hardy-con-un.html](http://blockdeubuntu.blogspot.com/2008/08/conexin-wifi-en-ubuntu-hardy-con-un.html)

Saludos.

---

### Post by CdK1 on 2010-01-08
Sigue estos pasos:

sudo apt-get install b43-fwcutter
cd /usr/share/b43-fwcutter
sudo ./install_bcm43xx_firmware.sh

---

### Post by moreback on 2010-01-08
¿No debería aparecer en **Sistema -> Administración -> Controladores de hardware**?

---

### Post by Iced1 on 2010-01-08
Muchas gracias a los dos porfin pude, yo al principio pense que era algo dificil lo de NOAPIC, pero ahora que de claro, al principio no me sirvieron los controladores que me pasaste pero por que ubuntu no me dejaba activarlos sin conexion a internet asique tuve conectar el notebook directo con un cable y asi poder tener conexion a internet y poder activar el controlador, lo reinicie y me reconocio wifi, bueno de nuevo muchas gracias ya que sin su ayuda no podria haberlo hecho.

---

### Post by moreback on 2010-01-08
Por problemas de licencia de los drivers de esas tarjetas tienen que ser descargados por los usuarios y no pueden ir en los cds de Ubuntu. Es por eso que la aplicación Controladores de hardware necesita una conexión a Internet para descargar esos firmwares.

Saludos.

---

### Post by CdK1 on 2010-01-08
Solved

---

