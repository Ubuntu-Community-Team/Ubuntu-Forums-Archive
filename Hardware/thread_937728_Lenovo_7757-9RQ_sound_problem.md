---
title: "Lenovo 7757-9RQ sound problem"
date: 2008-10-04
forum: Hardware
---

### Post by aazamansari on 2008-10-04
Hi,

I bought a Lenovo Laptop series 7757-9RQ.

I installed Ubuntu on it and did updated it. When I did sound testing I don't hear any sound from the system. Also when I play some MP3 file the player seems to play the file but I don't hear any sound from the system.

I did following:
cat /proc/asound/card0/codec#* | grep Codec

sudo gedit /etc/modprobe.d/alsa-base

and Added following line:
options snd-hda-intel model=lenovo

and rebooted. Still the sound doesn't work.

Then I did following:
cat /proc/asound/card0/codec#* | grep Codec

It showed 2 Codecs:

Realtek ALC260
Motorola Si3054

Then I tried replacing lenovo by above two one by one and rebooted but still it doesn't work.

options snd-hda-intel model=Realtek ALC260


Do I need to install driver for sound?
Please tell me what I need to check?


Thanks,
Azam.

---

### Post by aazamansari on 2008-10-18
Guys when I use
options snd-hda-intel model=lenovo-3000

the sound works but with strange behaviour.

On restarting the system I have to go to sleep mode and then and again restart. If I do this the sound works. Again if I restart the system the sound stops.

Any idea what is happening?

---

