---
title: "Kmix: Mixer cannot be found"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by Heretic09 on 2005-05-28
I have a 2545 xcdt toshiba laptop with kubuntu installed. It has a yamaha sound chip and I can hear the startup sound when kde loads. I can also play mp3s and wav files just fine. Kmix though has a little red X next to it and gives the message "Mixer cannot be found". I have mixer and mixer 1 in the /dev directory. Is there any way to get kmix see my soundcard?

---

### Post by ::DoGG:: on 2005-05-29
You probably need to install some additional packages. I had the same problem when tried alsa and i just installed packages with "alsa" and "mixer"  word form repo and worked :D

---

### Post by Heretic09 on 2005-05-29
Tried that, still doesn't show up in kmix. Does kmix have any config files I can manually edit so I can point it to the mixer device?

---

### Post by ::DoGG:: on 2005-05-29
Do You have alsamixer instaleld ? it`s a shell application. try this one.

---

### Post by Heretic09 on 2005-05-29
alsamixer gives the error:

alsamixer: function snd_ctl_open failed for default: no such file or directory

---

