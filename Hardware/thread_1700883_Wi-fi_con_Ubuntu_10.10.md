---
title: "Wi-fi con Ubuntu 10.10"
date: 2011-03-05
forum: Hardware
---

### Post by Feedehh on 2011-03-05
Buenas, anoche me decidi instalar Ubuntu 10.10 en mi Notebook Dell Inspiron 1440, todo bien al principio, pero no me puedo conectar a traves de Wi-fi. En "Controles Adicionales" me aparece "Controlador Inalambrico Broadcom STA" y dice que el controlador esta activado y se esta usando actualmente. El problema es que cada vez que quiero conectarme a mi Red Wi-fi me pide la contraseña una y otra vez, pero se que la estoy poniendo bien. Despues de tres intentos, me dice que la red inalambrica esta desconectada. Muchas gracias!

---

### Post by hectorivand on 2011-03-05
> **Feedehh said:**
> Buenas, anoche me decidi instalar Ubuntu 10.10 en mi Notebook Dell Inspiron 1440, todo bien al principio, pero no me puedo conectar a traves de Wi-fi. En "Controles Adicionales" me aparece "Controlador Inalambrico Broadcom STA" y dice que el controlador esta activado y se esta usando actualmente. El problema es que cada vez que quiero conectarme a mi Red Wi-fi me pide la contraseña una y otra vez, pero se que la estoy poniendo bien. Despues de tres intentos, me dice que la red inalambrica esta desconectada. Muchas gracias!

Hola Fede, podes poner el resultado del siguiente comando?

```
lsusb
```

Saludos
Nacho

---

### Post by Feedehh on 2011-03-05
Esto es lo que me dio el comando:
```

feedehh@feedehh-Inspiron-1440:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1ea7:000b  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:6400 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Muchas gracias.

---

### Post by hectorivand on 2011-03-05
Proba con 

```
lspci
```

Quiero tener el modelo exacto de la placa wireless.

Saludos
Nacho

---

### Post by Feedehh on 2011-03-05
Aca esta el otro comando:

feedehh@feedehh-Inspiron-1440:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

Muchas gracias.

---

### Post by hectorivand on 2011-03-05
Proba con esto...

[http://akebuntu.comyr.com/instalar-broadcom-bcm4312-en-ubuntu/](http://akebuntu.comyr.com/instalar-broadcom-bcm4312-en-ubuntu/)

También podes probar con este también.

[http://ubuntuforums.org/showthread.php?t=1312873](http://ubuntuforums.org/showthread.php?t=1312873)

Sencillito, comentame que onda.

Saludos
Nacho

---

### Post by Feedehh on 2011-03-05
No, sigue sin funcionar :(

Edito: Desactive el controlador STA por Contoladores Adicionales, Reinicie y me aparecieron dos controladores: el STA y un "Broadcom B43 wireless driver", pero al instalar ese controlador aparece "SystemError: InstallArchives() Failed".

---

### Post by asterix77 on 2011-03-07
Tengo esa misma tarjeta de red, deshabilité el driver STA porque me daba algunos errores de vez en cuando, por lo que activé el driver b43.

Para extraer el firmware de esa tarjeta, es necesario primero tener instalado el paquete b43-fwcutter.

Es recomendable que primero te conectes vía cable a internet para descargar e instalar todo. Te vas a un aconsola (o Synaptic si prefieres) y lo instalas.

$sudo apt-get install b43-fwcutter

Debieran aparecerte dos controladores para esa tarjeta cuando te vas a:

Sistema----->Administración------->Controladores de Hardware

a) Broadcom b43 wireless driver
b) Controlador inalámbrico Broadcom STA

Aqui debes desactivar el Broadcom STA, y activar el b43 tras lo cual se comienza la descarga del controlador.


Te dejo un link que te puede servir también.

[http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx](http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx)


Saludos

---

### Post by Feedehh on 2011-03-07
Muchas gracias por su ayuda. Al final era un problema de claves, no me entere hasta que no desconfigure el Router por completo :lolflag:
Muchas gracias de todas formas!

---

