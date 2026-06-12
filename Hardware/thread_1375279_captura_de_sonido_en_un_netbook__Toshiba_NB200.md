---
title: "captura de sonido en un netbook  Toshiba NB200"
date: 2010-01-07
forum: Hardware
---

### Post by donmatas on 2010-01-07
Estimad@s:
soy un inexperto que siempre anda tratando de liberar computadoras pese a mis escasos conocimientos. En esta ocasión se t00rata de un netbook toshiba N200 que ha resultado bien ****** (hay un extenso hilo al respecto en el foro en inglés. Cuento corto: después de arduas dificultades para instalar el UNR yel 9.10 logré finalmente hacerlo funcionar con 9.04 normal. Lamentablemente no he podido hacer fucionar la captura de sonido (esencial para skype).
les mando el lspci para ver si me pueden dar una manito
gracias de antemano

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
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
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by donmatas on 2010-01-08
Estimad@s:

logré capturar sonido, al menos con el mic incorporado, pero con bastante ruido. Fui a Sistema/Preferencias/Sonido y ahí seleccioné la opción "OSS - Open Sound System" en "Captura de Sonido" dentro de "Conferencia de Sonido" en la pestaña de "dispositivos"

suerte!

DM

---

