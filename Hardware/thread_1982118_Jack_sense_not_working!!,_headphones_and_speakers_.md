---
title: "Jack sense not working!!, headphones and speakers at the same time"
date: 2012-05-18
forum: Hardware
---

### Post by JohnFrank951 on 2012-05-18
Hi!
I have  a Panasonic cf-74 tough-book  (laptop) , my headphones doesn't mute the speakers! It is quite frustrating the fact that i couldn't fix the problem...

I  try to add a line like the following :

"options snd_hda_intel model=xxxxxx"    in   "/etc/modprobe.d/alsa-base.conf"
(the xxxxx is where i am supposed to put a specific module for my chip)

when i type in the console: 

"aplay -l " it show me something like this:


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


i search AD198x in this list :   
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)
but i couldn't find the right module... i really need some help please, 


Thanks!

---

