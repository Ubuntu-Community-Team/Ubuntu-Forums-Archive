---
title: "Sound Issues in 8.10"
date: 2009-01-04
forum: Hardware
---

### Post by Darkdelusions on 2009-01-04
I recently installed 8.10 on my laptop and seem to running to a small annoying issue with sound. When I plug in my headset what ever i am listening to plays threw both my laptop speakers and the headset and I for the life of me can not figure out how to fix it.

---

### Post by Darkdelusions on 2009-01-19
I still have not found a successful fix for this issue below are the following things I have tired. 

I have edited the alsabase file and added. 

```
options snd-hda-intel model=3stack
```

then I tired 
```

options snd-hda-intel model=asus
```

and lastly 

```
options snd-hda-intel model=auto

```

So at this point I have run out of options below is my aplay info and my model number. 

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Model: Asus m50sv-b1

---

### Post by Darkdelusions on 2009-01-19
Solved thanks to [http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)

---

