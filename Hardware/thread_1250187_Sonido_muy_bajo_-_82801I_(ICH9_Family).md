---
title: "Sonido muy bajo - 82801I (*ICH9 Family*)"
date: 2009-08-26
forum: Hardware
---

### Post by Tosh78 on 2009-08-26
Hola! Instale Ubuntu 9.04 en una laptop y al principio no tenia sonido. Despues, agregue:

options snd-hda-intel model=dell-m6

al archivo alsa-base.conf

Ahi logre que se escuchara, sin embargo el volumen esta bajo y ya subi todos los volumenes. Alguien me puede dar una mano?

El lspci me devuelve esto:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

lo cual me desconcierta un poco porque primero dice:

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Y despues dice:

Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

Bueno, cualquier ayuda es bienvenida. 

Gracias!

---

### Post by faktorqm on 2009-08-27
Hola, tengo entendido que es un problema "comun", quiero decir, que se encuentra este efecto en este tipo de hardware comunmente. 

Como solucion lo que propondria es recompilar alsa, para descartar fehacientemente cualquier tipo de problema o duda acerca del driver, y/o algun bug de él. Si eso no mejora el problema, lamentablemente creo que vas a tener que esperar a KK en octubre....

Respecto del "sonido de la placa de video" supongo que es una salida de sonido que viene en la placa, por ejemplo la mia trae para salida de super video, que viaja con audio, ergo aparece un dispositivo como tal. 

Si no sabes como hacer algo, consulta. Salu2!

---

### Post by Tosh78 on 2009-08-27
Hola Faktor! 
Muchas gracias por responder. Sabia que eras la persona que podia ayudarme.
Voy a intentar recopilar ALSA, ahora, una pregunta: cuando actualice a KK, voy a tener que recompilarlo otra vez o deberia quedar funcionando?

Muchas gracias!

---

### Post by Tosh78 on 2009-08-29
No hay caso che, recompile el driver de ALSA y sigue teniendo sonido bajo. Alguna otra sugerencia? Los volumenes con ALSA mixer estan al maximo

---

### Post by Tosh78 on 2009-09-03
Bueno, pude solucionar el problema. Lo posteo por si a alguien le sirve. Instale KMIX, lo ejecute y dandole boton derecho, canales, seleccione la opcion de Master. Eso aumento muchisimo el volumen.

---

