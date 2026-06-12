---
title: "How to make your headphones work (and the speakers mute)"
date: 2009-04-30
forum: Hardware
---

### Post by agnes on 2009-04-30
Hello everyone,

it was very hard for me to find this fix online, so I post it here, that it may be found easier by people. 

Ubuntu did not play through my headphones (while muting the speakers) when I plugged them in, only when I already had them plugged in while booting my laptop. 
This must stem from some sort of isue that Ubuntu/Alsa does not automatically detect your laptop brand.

To fix this I had to put the line ```
options snd-hda-intel model=hp 
``` in the file _/etc/modprobe.d/alsa-base_. 

You should replace 'hp' by your laptop/PC brand, e.g. if you have a sony vaio you should replace 'hp' by 'vaio'. For the rest of the brands I don't know, just fill in the obvious I would say.

Then restart.

Greetings

---

