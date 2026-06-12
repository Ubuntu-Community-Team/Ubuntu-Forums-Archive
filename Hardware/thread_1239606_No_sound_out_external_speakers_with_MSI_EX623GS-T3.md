---
title: "No sound out external speakers with MSI EX623GS-T3443VH"
date: 2009-08-13
forum: Hardware
---

### Post by hierkommtdiemaus on 2009-08-13
Hello everyone, 

just bought a MSI EX623GS-T3443VH notebook, and installed ubuntu 9.04. The problem is the sound. I do get sound from the headphone line-out, but none from the external speakers and the subwoofer. 

I read through the sound troubleshooting, aplay -[FONT=Verdana]l brings

 [/FONT]> 
Karte 0: Intel [HDA Intel], Gerät 0: ALC1200 Analog [ALC1200 Analog]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC1200 Digital [ALC1200 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
 

Yes, it is german, but I guess you will understand it. 

Then 

head -n 1 /proc/asound/card0/codec*	

brings 

> 
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040



My alsa infos are these:

[http://www.alsa-project.org/db/?f=0a3ad701f8efcf642b72c70fb7f1cab153b1cfed](http://www.alsa-project.org/db/?f=0a3ad701f8efcf642b72c70fb7f1cab153b1cfed)

The last option in my alas-base.conf is 

options snd-pcsp index=-2

but I dont really know how what to change it to, since the codec does not show up in the alsa configuration.txt

Any help?

Cheers,
Jan

---

