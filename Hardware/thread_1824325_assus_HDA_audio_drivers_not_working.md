---
title: "assus HDA audio drivers not working"
date: 2011-08-13
forum: Hardware
---

### Post by surajrajpurohit on 2011-08-13
i'm using asus mother board which is having nvidia HDA audio. I found from nvidia website that hda intel drivers will work. 
the current drivers in my ubuntu is 

cat /proc/asound/card0/codec* | grep Codec
Codec: VIA VT1708S

i've followed the instructions from [https://help.ubuntu.com/community/HdaIntelSoundHowt](https://help.ubuntu.com/community/HdaIntelSoundHowt)

In sudo nano /etc/modprobe.d/alsa-base.conf

i've added 

options snd-hda-intel model=ALC880

sudo alsa force-reload

also got the model number from the link in [https://help.ubuntu.com/community/HdaIntelSoundHowt](https://help.ubuntu.com/community/HdaIntelSoundHowt)
...
and rebooted but its not working

i've alsodownloaded alsa-drivers-10 from alsa website
i've downloaded .tar.bz2 file
den i've unziped it and complied the drivers
but this is also not working
after reboot i again got the old drivers

---

