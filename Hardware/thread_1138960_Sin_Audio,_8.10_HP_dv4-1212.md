---
title: "Sin Audio, 8.10 HP dv4-1212"
date: 2009-04-26
forum: Hardware
---

### Post by NoaH76 on 2009-04-26
Bueno tengo una hp dv4-1212 con ubuntu 8.10 y no hay sonido.

fran@NoaH:~$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
fran@NoaH:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: ATI HDMI [ATI HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


Gracias

---

### Post by antiriad on 2009-04-27
hola,
yo tengo la misma notebook y con esto me anduvo:


1-editar la configuracion de alsa



para kubuntu:

sudo kate /etc/modprobe.d/alsa-base.conf


para ubuntu:
gksudo gedit /etc/modprobe.d/alsa-base.conf




 2- anda al final del archivo y agrega


 options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1


3- reinicia... y funca :D


saludos

---

