---
title: "Problemas con el sonido"
date: 2008-05-18
forum: Hardware
---

### Post by atari130xe on 2008-05-18
Gente acá estoy nuevamente, ahora con banda "chancha" (no puedo creer la dif. con Dial Up! jejeje). Resulta ser que compré una nueva PC, instalé Hardy y el sonido para todo lo que es reproducción de música y video funciona perfecto, pero no logro hacer que pase lo mismo con los Juegos (SuperTux, Frozen bubble, etc), "cero sonido" como si no detectaran la placa de sonido. Haciendo un lspci obtengo:
```
 lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

```
Tengo sonido integrado a la placa madre en este caso. Cambié las opciones en Sistema --> Preferencias --> Sonido y elegí: PnP audio device (Alsa mixer) y nada, probé con SAA7134 (Alsa mixer) y nada tampoco, estoy un poco desorientado. alguna sugerencia?:)

---

### Post by atari130xe on 2008-05-18
Nadie para orientarme sobre esto? es raro pero no consigo encontrarle la vuelta y por ahi es algo simple, gracias!:(

---

### Post by faktorqm on 2008-05-19
saa7134 debe ser tu placa capturadora, asi que ahi no va a sonar nunca...
dependiendo de cada juego usan distintos servers, segun tengo entendido, usan oss o el ex-esd, ahora pulseaudio. proba en preferencias -> sonido cada server con el boton "probar" que tenes a la derecha, y VERIFICA que todos los volumenes esten "arriba" y no tengas nada en mute. Salu2!!

---

### Post by atari130xe on 2008-05-19
Nop no hay caso, por ahí el chip de sonido no es compatible:
El mother es:
Asus M2N-SLI el audio integrado es: C-Media 7.1 channel audio codec.
A veces funca como USB Audio, otras como ALSA, otras como PnP audio device, me desconcierta, acabo de bajar LastFm y no logro escuchar nada, la verdad que ni idea.

---

### Post by qntal on 2008-05-19
no tendras los volumenes bajos con pulse audio?

---

### Post by atari130xe on 2008-05-19
No, veo el control (Master) y esta a tope. por ejemplo estoy escuchando música ahora mismo con Xmms y chequeo control de volumen:
Control de volumen: Playback: ALSA PCM on front:1 (USB AUDIO) VIA DMA (PULSEAUDIO MIXER), la musica suena perfecto pero el resto no... :confused:

---

### Post by gertlm on 2008-05-19
hola, probaste en el control de volumen al lado del reloj, hacer click con el boton derecho preferencias y seleccionar el control de tu placa de audio la mia es una via y en el control dice VIA 8235 (Alsa mixer)

Por ahi tenes problemas con el sonido, porque hay programas que usan una placa y otros te estan usando la otra, fijate tambien en preferencias -> sonidos
en la parte de dispositivos ponele a mano la placa de sonido en cada categoria

---

### Post by atari130xe on 2008-05-22
Bueno, por lo visto parece que no soy el ùnico con ese problema pero hasta ahora y luego de "Googlear" un toco no le encuentro la solucion, mi mother es un ASUS M2N SLI el chip integrado es el C-Media 6501 (usb), suena el XMMS, suena el emesene, pero los juegos CERO, voy a reinstalar el SO y verè que hago... gracias de todas maneras, estos desafios de hacer funcionar hardware con pesados a veces pero al menos lo intento.

---

### Post by osensei on 2008-05-23
Hola, fijate si este thread te sirve: [http://ubuntuforums.org/showthread.php?t=804026](http://ubuntuforums.org/showthread.php?t=804026)

Saludos!

---

