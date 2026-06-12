---
title: "Toshiba Satellite L35 SP1011 sin sonido"
date: 2010-05-19
forum: Hardware
---

### Post by cantervilotis on 2010-05-19
Estimados:

Acabo de instalar Lubuntu Lucid Lynx en un Toshiba Satellite L35 SP1011 y no tengo sonido.

La salida de $lspci es:

> *00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
**00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)**
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+(rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)


Probé con

> sudo gedit /etc/modprobe.d/alsa-base (se abrió un archivo vacío) 
Al cual se le agregó 
> options snd-hda-intel model=dallas (sin resultado)

Lyego se volvió a editar  sacando lo anterior y agregando > options snd_hda_intel model=uniwill-m31
Esto último da resultado pero el sonido se queda "pegado".

Ví este post [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) pero no esa dispnible para lucid lynx, servirá alguno de ellos?

Saludos atentos

---

### Post by Carlos C on 2010-05-27
Te sugiero partir por lo más simple, aunque suene evidente. En el terminal escribe:
```
alsamixer
```
y verifica que todos los volúmenes estén arriba.

Saludos.

---

### Post by nopalux on 2010-09-17
Que tal, tengo el mismo problema con las caracter{sticas de equipo de la persona que abrio el tema. Alguna idea, aparte de lo mas simple. Gracias

---

