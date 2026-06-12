---
title: "Jaunty - Problemas sonido"
date: 2009-06-22
forum: Hardware
---

### Post by llove on 2009-06-22
Hola estoy teniendo problemas con el sonido, apenas inicia la maquina me anda perfecto, todas las placas de sonido, pero luego de un rato, o luego de reiniciar una aplicacion que use sonido, generalmente Mixxx, pierdo el sonido de la placa onboard. Sinceramente nose que mas probar, Jaunty un problema atras del otro me esta trayendo. Esto me muestra aplay -l.

ariel@ariel-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


-----------------------------------------------------------------------------

luego, cuando la placa onboard no funciona, cambia a esto.

card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0



Si necesitan que postee algo mas, avisen.

Saludos

ps: tampoco soluciona nada reiniciar alsa, o bien cargar de nuevo el modulo snd-hda-intel, solo se soluciona reiniciando la maquina, y vale aclarar que es el tercer clean install que hago en el mes. Sin mencionar que en Intrepid no tenia este problema. Gracias.

---

### Post by pablo.s on 2009-06-22
Deshabilita en la BIOS
a la placa onboard.

---

### Post by llove on 2009-06-22
no me quedaria sin sonido asi???? uso las dos placas, ese es el tema, la Audigy cero dramas igualmente.

---

### Post by pablo.s on 2009-06-22
Los programas que utilizas,
dependen de ALSA o de
PulseAudio? A veces hay
conflicto entre ellos y se 
arregla deshabilitando
PulseAudio.

---

### Post by llove on 2009-06-22
alsa, o bien oss, este ultimo funciona bien, podria usarlo asi, pero me gustaria saber porque me pasa eso con alsa. 

ps: como deshabilito pulse? desinstalo todos los paquetes?

---

### Post by pablo.s on 2009-06-22
Aca hay [informacion]("https://wiki.ubuntu.com/PulseAudio").

---

