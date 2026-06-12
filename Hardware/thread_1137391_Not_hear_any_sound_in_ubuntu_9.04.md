---
title: "Not hear any sound in ubuntu 9.04"
date: 2009-04-25
forum: Hardware
---

### Post by jamal2009 on 2009-04-25
hi when i install the ubuntu ver 8 all hardware compatibly with this systems but when i see in your site that ready to download the 9.4 i install it and i seprice that i did not hear any sound from anay files i do that command in terminal 

-laptop:~$ aplay -l shows
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and i see that my hardware is installing ready to use can some one help me plz to can i hear sound from notebook 

thanks

---

### Post by marcoslai on 2009-04-26
Open terminal,key in: sudo gedit /etc/modprobe.d/alsa-base.conf

Insert the following :

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel

save & restart.

---

