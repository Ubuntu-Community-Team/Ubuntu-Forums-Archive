---
title: "ayuda con mi memory stick"
date: 2010-05-26
forum: Hardware
---

### Post by Felipexs on 2010-05-26
hola, soy nuevo en este foro soy chileno, bueno resulta que llevo bastante tiempo con mi ubuntu, ahora estoy usando la nueva 10.04 y cuando quise conectar el memory stick no me funciono osea no iso nada de nada mi notebook es un hp pavilion dv2621la por fa ayúdenme llevo bastante tiempo sin solucionar este problema

---

### Post by Carlos C on 2010-05-27
Hola. Por favor copia acá el resultado del comando "lspci". De esa forma sabremos el modelo del controlador de tu lector de tarjetas. Si es una Texas instrument debiera funcionar en Ubuntu. Si es una "Ricoh" entonces no:

[https://answers.launchpad.net/ubuntu/+faq/312](https://answers.launchpad.net/ubuntu/+faq/312)

Esta información es de hace bastante tiempo, así que es posible que el escenario haya cambiado. Te sugiero que busques con google información mas actualizada.

Saludos.

---

### Post by bichopro on 2010-05-27
Independiente del hardware se supone que la memory stick de sony tiene un firmware propietario y no hay controlador libre para linux a diferencias de las sd o las xd que funcionan sin ningun problema. Yo tengo una camara sony y la unica forma es enchufarla con el cable mini usb al pc

---

### Post by Carlos C on 2010-05-27
> **bichopro said:**
> Independiente del hardware se supone que la memory stick de sony tiene un firmware propietario y no hay controlador libre para linux a diferencias de las sd o las xd que funcionan sin ningun problema. Yo tengo una camara sony y la unica forma es enchufarla con el cable mini usb al pc

Otra opción es comprar un adaptador y transformarlas en un pendrive.

---

### Post by Felipexs on 2010-05-27
bro.. me salio esto
 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960  Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI  Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio  Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI  Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface  Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E)  IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E)  SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller  (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E  Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN  (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller  (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro  Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev  12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host  Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev  ff)

---

### Post by Carlos C on 2010-05-28
Creo que es una Ricoh y por lo tanto no habría soporte para ese tipo de tarjetas en Linux.

---

### Post by Felipexs on 2010-05-29
Guau eso si que es un problema grande :confused::confused::confused::confused::confused::confused::confused:
no sabes como solucionarlo

---

### Post by Carlos C on 2010-05-30
puedes comprar un adaptador y conectarla al puerto usb. Es lo único que se me ocurre.
Saludos.

---

