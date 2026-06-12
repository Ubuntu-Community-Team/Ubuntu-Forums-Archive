---
title: "Problemas con audio en Xubuntu 10.04"
date: 2010-05-06
forum: Hardware
---

### Post by Tomito on 2010-05-06
Hola gente...

Bueno el tema es que quiero quedarme con Xubuntu 10.04, pero tengo un problema con el audio. No suena nada, la tarjeta de sonido es reconocida, pero no tengo ningún tipo de audio.
Cabe decir que antes probé Ubuntu 10.04 y no tuve problemas, aquí les dejo mi salida lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:08.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

Al probar alsamixer por consola se vé todo bien, a niveles de aprox 70% pero no pasa nada, alguna sugerencia que me puedan dar

Saludos

---

### Post by sXeChris on 2010-05-06
Debes poner este post en el forum que esta en espanol.

---

### Post by bichopro on 2010-05-06
> **sXeChris said:**
> Debes poner este post en el forum que esta en espanol.
Esta en foro de chile que esta en español!

Ejecuta este comando en el terminal:

> alsamixer -Dhw

muévete con las flechas del teclado y busca alguna que este baja o en cero subela y prueba.

---

