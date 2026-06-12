---
title: "[SOLVED] Intel HDA - Intel Corporation 82801G - No Sound"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by Urban Druid on 2007-12-01
Ok, here's how I Stand...

[LIST]
[*]Fresh installation of Ubuntu...
[*]Intel Hda card...
[*]Works perfectly on both openSUSE and Windows XP
[/LIST]

I get no sound from my laptop at all unless I run the line out to my guitar amp, which is set to max. then I hear everything as if through headphones placed a meter away, real quiet. Its an 80w amp.

The command "aplay -l" retrieves this:#

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0





I have looked at the alsamixer in the terminal, and get this...

[IMG]http://i236.photobucket.com/albums/ff184/yozpul/alsamixer.png[/IMG]



When I try to increase "IEC958", nothing happens.


If there is any more info I need to provide, I will be more than happy to do so.

Any help will be much appreciated...

Thanks

Urban Druid

---

### Post by Urban Druid on 2007-12-02
Sorted, 

Take a look at [http://ubuntuforums.org/showthread.php?t=537676&highlight=%5Bsolved%5D+toshiba]("http://ubuntuforums.org/showthread.php?t=537676&highlight=%5Bsolved%5D+toshiba") for the fix

---

