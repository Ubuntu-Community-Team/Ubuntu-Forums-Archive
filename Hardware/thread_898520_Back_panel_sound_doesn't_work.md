---
title: "Back panel sound doesn't work"
date: 2008-08-23
forum: Hardware
---

### Post by jkyahoo101 on 2008-08-23
When I boot into Ubuntu my speakers don't work when they are connected to the back of my panel. But when I connect them to the front of my computer they work. How can I get the back panel to work in Ubuntu?

---

### Post by jkyahoo101 on 2008-08-31
Does anyone know?

---

### Post by jkyahoo101 on 2008-09-13
Can someone please point me in the right direction at least?

---

### Post by eggdeng on 2008-09-13
Post the output of ```
aplay -l
``` and the make and model of your box. If you get ```
Intel [HDA Intel]
``` google or do a forum search for your make and model to see if anyone else has had the same problem.

---

### Post by jkyahoo101 on 2008-09-14
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by eggdeng on 2008-09-14
> and the make and model of your box8-)

---

### Post by markbuntu on 2008-09-14
Check in the switches section of the volume control or sound mixer. You can also try this thread here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by jkyahoo101 on 2008-09-28
Its a custom pc.

---

### Post by markbuntu on 2008-09-28
Then you just need to try the options for ALC883 until you find the one that works for you.

---

