---
title: "Sound Card Specs"
date: 2008-09-08
forum: General Help
---

### Post by Th3Professor on 2008-09-08
Hi!

I'm running Ubuntu Studio on a Toshiba Satellite A205-S5855, have checked various outputs (lspci, dmesg) for audio specs though limited information comes up. I checked Toshiba's site and various other sites for system specs. I have several of the other specs though am looking for very specific, completely detailed, information on the audio and sound card. Any ideas how to retrieve that information?

Thanks!

-Prof

---

### Post by eggdeng on 2008-09-08
```
 sudo lshw -class multimedia
``` for info on the hardware.
```
asoundconf list
```
and
```
aplay -l
```
for info on how alsa recognises your device(s).

---

### Post by Th3Professor on 2008-09-08
Thank you!

---

### Post by eggdeng on 2008-09-09
Just one more
```
cat /proc/asound/devices 
```will give you info on the components of each device.

---

