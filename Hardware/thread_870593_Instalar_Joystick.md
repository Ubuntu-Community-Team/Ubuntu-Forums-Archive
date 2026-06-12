---
title: "Instalar Joystick"
date: 2008-07-26
forum: Hardware
---

### Post by h9005 on 2008-07-26
Buenas a todos tengo un joystick genius maxfire g-08 y no puedo hacerlo andar en ubuntu 8.04 studio. Como hago?

---

### Post by Hei Ku on 2008-07-26
Fuiste a la opcion del sistema de joystick? Te aparece algo?
Si no, postea aca que te sale cuando pones lsusb en la terminal.

---

### Post by h9005 on 2008-07-26
Pasa que es un joystick que se conecta al puerto midi de la placa de sonido pci (una soundblaster). No es usb.

---

### Post by eldragon on 2008-07-26
quiza esto te sirva: [http://onlyubuntu.blogspot.com/2007/03/how-to-set-up-gameportgamepad-or.html](http://onlyubuntu.blogspot.com/2007/03/how-to-set-up-gameportgamepad-or.html)

esta en ingles, pero es algo...

---

### Post by Hei Ku on 2008-07-26
entonces pone lspci. Eso lista todos los dispositivos conectados a traves de pci.

---

### Post by h9005 on 2008-07-26
lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

Todo eso es lo que me sale. Es el puerto sur?

---

### Post by Hei Ku on 2008-07-26
Fijate en este thread:

[http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

Tenes instalados los paquetes joystick y jscalibrator?

---

### Post by h9005 on 2008-07-27
Ok me fijo. Si lo instale.

---

