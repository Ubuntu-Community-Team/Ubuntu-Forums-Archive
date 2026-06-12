---
title: "Problemas en la placa de audio"
date: 2009-02-04
forum: Hardware
---

### Post by duricio on 2009-02-04
Hola, gracias de antemano por la ayuda q me puedan dar.
Les comento que tengo 2 placas de audio instaladas en mi pc y no las puedo hacer funcionar en Ubuntu(recien instalado).
Tire estos comandos para que vean que es lo que tengo y ver si me pueden tirar una soga.
gracias.

:aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: AudioPCI [Ensoniq AudioPCI], dispositivo 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: AudioPCI [Ensoniq AudioPCI], dispositivo 1: ES1371/2 [ES1371 DAC1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0




 :lspci | grep -i audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
01:06.0 Multimedia audio controller: Creative Labs Ectiva EV1938

:D

---

### Post by duricio on 2009-02-04
He instalado el ALSA-Driver-1.0.19, ALSA-utils-1.0.19, ALSA-oss-1.0.19 y ALSA-lib- 1.0.19.
Slds

---

### Post by pablo.s on 2009-03-11
Hola: Te recomiendo algo: si no vas a utilizar las DOS placas, probá con deshabilitar la placa onboard de Nvidia en la BIOS y solamente usá la Creative Ectiva. Saludos.

---

