---
title: "[AYUDA] Presario SR5020LA Problema de audifonos y parlantes."
date: 2009-09-08
forum: Hardware
---

### Post by homosapiens999 on 2009-09-08
Hola soy nuevo en este foro, y estoy aquí humilde e ignoantemente solicitando ayuda sobre un problema que tengo en mi maquina.

El problema es que al conectar los audifonos a la parte delantera de mi gabinete las bocinas siguen sonando, y los audifonos tambien, osea que los audifonos no silencian la salida de las bocinas cuando los coencto, como si no detectara que conecto los audifonos.

Instale el programa que dicen que hay que poner antes de pedir ayuda y aqui pongo la informacion de audio que me dió.

```

Escritorio:    GNOME

```


```

$lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

```


```

$aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC888 Analog [ALC888 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```


```

$lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```


```

$asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel

```


```

$cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 16

```


```

$lsmod | grep -i snd
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd

```


```

$lsof /dev/snd/controlC0 /dev/snd/pcmC0D0c /dev/snd/pcmC0D0p /dev/snd/pcmC0D1p /dev/snd/pcmC0D2c /dev/snd/seq /dev/snd/timer
COMMAND    PID           USER   FD   TYPE DEVICE SIZE  NODE NAME
pulseaudi 4247 homosapiens999   23u   CHR  116,7      16258 /dev/snd/controlC0
pulseaudi 4247 homosapiens999   30u   CHR  116,7      16258 /dev/snd/controlC0
mixer_app 5486 homosapiens999   22r   CHR  116,7      16258 /dev/snd/controlC0

```


Espero y puedan ayudarme. GRacias!!:)

---

### Post by Carlos C on 2009-09-20
En general este tipo de problemas se solucionan añadiendo una linea a tu archivo /etc/modprobe.d/alsa-base.conf. Hasta donde sé siempre es del tipo:

```
options snd-hda-intel model=MODEL
```

Donde MODEL cambia para cada equipo. El problema es saber qué parámetro corresponde a tu caso. Te sugiero que mires el siguiente thread, no encontré tu modelo específico pero puede que alguno te sirva:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

También puedes mirar acá, está en aleman, pero de todas maneras la tabla se entiende:

[http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA](http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA)

Más información en Ubuntu Documentation:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Tendrás que tener paciencia y buscar la opción que te sirva. Por favor, en caso de que resuelvas tu problema no olvides decirnos cómo lo hiciste.

Saludos.

---

