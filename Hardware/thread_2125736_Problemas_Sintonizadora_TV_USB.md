---
title: "Problemas Sintonizadora TV USB"
date: 2013-03-14
forum: Hardware
---

### Post by Leandro17 on 2013-03-14
Hola, vengo a comentarles un problema que tengo desde [hace bastante tiempo]("http://ubuntuforums.org/showthread.php?t=1530572") y todavia no lo he solucionado.

La cuestion es la siguiente, tengo una placa externa usb sintonizadora de television y radio, marca Kaiomy modelo tvnpc u2 pro, que hasta el dia de hoy no logre ver television con ella en Ubuntu. Seguí todas las sugerencias que me dieron en su momento y aun no pude hacerla funcionar (o mas bien configurar). Y como pasaron un par de años vuelvo a plantear el problema para ver si por fin puedo ver television.

En estos momentos tengo instalado Ubuntu LTS 12.04 con kernel 3.4.3-030403-generic
Al hacer lsusb en el terminal me devuelve lo siguiente:

```
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 002 Device 002: ID eb1a:2863 eMPIA Technology, Inc. Video Grabber
Bus 007 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Siendo: *Bus 002 Device 002: ID eb1a:2863 eMPIA Technology, Inc. Video Grabber* mi placa.

Con dmesg | grep em28 me devuelve lo siguiente

```
[   24.787909] em28xx: New device  USB 2863 Device @ 480 Mbps (eb1a:2863, interface 0, class 0)
[   24.787914] em28xx: Audio Vendor Class interface 0 found
[   24.787916] em28xx: Video interface 0 found
[   24.787917] em28xx: DVB interface 0 found
[   24.790286] em28xx #0: chip ID is em2860
[   24.920880] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 63 28 f0 00 65 03 6a 20 8a 0a
[   24.920887] em28xx #0: i2c eeprom 10: 00 00 24 57 4e 02 08 00 60 00 00 00 02 00 00 00
[   24.920893] em28xx #0: i2c eeprom 20: 1e 00 13 00 f0 10 01 82 82 00 00 00 5b 00 00 00
[   24.920899] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00
[   24.920905] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 c4 00 00
[   24.920911] em28xx #0: i2c eeprom 50: 81 00 00 00 00 00 00 00 00 c3 00 00 00 00 00 00
[   24.920917] em28xx #0: i2c eeprom 60: 11 00 00 00 00 00 00 00 00 00 20 03 55 00 53 00
[   24.920923] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 36 00 33 00 20 00 44 00
[   24.920929] em28xx #0: i2c eeprom 80: 65 00 76 00 69 00 63 00 65 00 0a 03 31 00 32 00
[   24.920934] em28xx #0: i2c eeprom 90: 33 00 34 00 00 00 00 00 00 00 00 00 00 00 00 00
[   24.920940] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   24.920946] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   24.920952] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   24.920957] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   24.920963] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   24.920969] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   24.920976] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xc143f201
[   24.920977] em28xx #0: EEPROM info:
[   24.920979] em28xx #0:	I2S audio, 3 sample rates
[   24.920980] em28xx #0:	500mA max power
[   24.920982] em28xx #0:	Table at 0x24, strings=0x206a, 0x0a8a, 0x0000
[   25.022627] em28xx #0: found i2c device @ 0xa0 [eeprom]
[   25.047623] em28xx #0: Your board has no unique USB ID.
[   25.047671] em28xx #0: A hint were successfully done, based on i2c devicelist hash.
[   25.047727] em28xx #0: This method is not 100% failproof.
[   25.047766] em28xx #0: If the board were missdetected, please email this log to:
[   25.047824] em28xx #0: 	V4L Mailing List  <linux-media@vger.kernel.org>
[   25.047872] em28xx #0: Board detected as EM2874 Leadership ISDBT
[   25.208035] em28xx #0: Identified as EM2874 Leadership ISDBT (card=77)
[   25.208134] em28xx #0: Config register raw data: 0xf0
[   25.208136] em28xx #0: I2S Audio (5 sample rates)
[   25.208137] em28xx #0: No AC97 audio processor
[   25.260024] em28xx #0: v4l2 driver version 0.1.3
[   25.812300] em28xx #0: V4L2 video device registered as video1
[   25.812303] em28xx #0: V4L2 VBI device registered as vbi0
[   25.836100] usbcore: registered new interface driver em28xx
[   26.460889] em28xx-audio.c: probing for em28xx Audio Vendor Class
[   26.460893] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   26.460894] em28xx-audio.c: Copyright (C) 2007-2011 Mauro Carvalho Chehab
[   26.952175] DVB: registering new adapter (em28xx #0)
[   26.952638] em28xx #0: Successfully loaded em28xx-dvb
```

Al ir a Configuración del sistema > Controladores adicionales
Me figura como activado el controlador *Empia em28xx based USB video device driver *

Viendo, *suponiendo*, que esta todo bien pruebo con algun programa. TVTime, MYTV, XBMC, MythTV. Pero nada, ni me dejan configurar, salvo MythTV que le pongo como device /dev/video1 y sigue sin pasar nada.

Lo que note si es que a veces, no siempre, cuando ejecuto algunos de estos programas aparece el cartel de que Ubuntu tuvo un problema, o algo asi.

Segui varios tutoriales y nada.

Que me sugieren??

---

