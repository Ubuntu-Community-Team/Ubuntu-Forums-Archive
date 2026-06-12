---
title: "ASUS M50VC sound card without sound"
date: 2008-10-23
forum: Hardware
---

### Post by nevcos on 2008-10-23
Hi all!

I've a new ASUS of M50VCseries.
The sound card is an Azalia (I think that is an Realtek chip) HD:

ASUS desc in site:
> Built-in Azalia compliant audio chip, with 3D effect & full duplex
Built-in 4 speakers and array microphone

from lspci -v:
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1893
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

from aplay -l:
> **** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Intel [HDA Intel], dispositivo 0: HDA Generic [HDA Generic]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

The problem is that there are no sound at all! I've just put all mixers up and loud, and put all without mute... I've tried the 2 phones outputs and the laptop speakers. Neither works... :S

In System > Preferences > Sound I have this devices listed:

[LIST]
[*]HDA Intel (Alsa mixer)
[LIST]
[*]Main
[*]PCM
[*]Capture
[*]Digital
[/LIST]
[*]Generic 10de ID 3 (OSS Mixer)
[LIST]
[*]Volume
[*]Ganho de entrada (Input gain)
[/LIST]
[*]Playback: Alsa PCM on front:0 (HDA Generic) via DMA (PulseAudio)
[LIST]
[*]Master
[/LIST]
[/LIST]

I've just have tried to change to all of them and nothing!

I really don't know what to do more... I can't get much info about this card.

Can you help me?

Thank you!

---

### Post by nixscripter on 2008-10-23
What happens when you open a terminal and run: ```
speaker-test
```

---

### Post by nevcos on 2008-10-24
The *speaker-test* result:

> 
speaker-test 1.0.15

Dispositivo de reprodução é default
Os parâmetros de fluxo são 48000Hz, S16_LE, 1 canais
A usar 16 oitavas de ruido cor-de-rosa
Taxa definida 48000Hz (pedida 48000Hz)
Tamanho do buffer vai desde 2048 a 16384
Intervalo de periodo de 1024 a 1024
Usando tamanho máximo de buffer 16384
Períodos = 4
period_sixe foi definido = 1024
foi definido tamanho_buffer = 16384
 0 - Frente Esquerda
Tempo por periodo = 2,664018
 0 - Frente Esquerda
Tempo por periodo = 2,986758
 0 - Frente Esquerda
Tempo por periodo = 2,986811

...

And absolutely no sound :(

In Windows, the sound is normal, witch removes the possibility of hardware problems, I think.

Cheers!

---

### Post by nixscripter on 2008-10-24
Well, that means (assuming that the numbers are in the same place as the english messages ;-)) the card is detected, and linux **thinks** it's driving it.

Now look at the levels in a command line utility, **alsamixer**. In particular, the Master, PCM, and Front Left (er, or whatever Esquerda is) levels should be checked. I am not sure what Gnome tries to link it to, so this is where I always start.

---

### Post by Yellow Pasque on 2008-10-24
See this post about configuring alsa-base file. [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

If that does not work, try building ALSA from source with this handy script:
[http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

The script is missing a dependency, so run this command before running the script:
```
sudo apt-get libasound2-dev
```

---

