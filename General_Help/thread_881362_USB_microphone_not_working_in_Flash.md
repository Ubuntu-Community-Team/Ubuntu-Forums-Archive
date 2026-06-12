---
title: "USB microphone not working in Flash"
date: 2008-08-05
forum: General Help
---

### Post by BWF89 on 2008-08-05
I have a Altec Lansing AHS433usb headset and it works fine with Skype but won't work when I try to chat on Stickam.

Any advice?

---

### Post by BWF89 on 2008-08-06
I installed Gnome ALSA Mixer and messed around with that but I'm still not able to get the mic to work in Flash programs.

---

### Post by BWF89 on 2008-08-06
Tried searching through all the topics on the subject and only came upon this: [http://ubuntuforums.org/archive/index.php/t-408453.html](http://ubuntuforums.org/archive/index.php/t-408453.html)

But I tried the commands and it just said "command not found".

---

### Post by BWF89 on 2008-08-07
I went into "/etc/modprobe.d/", opened "alsa-base" under sudo, and changed the following options:

options snd-usb-audio index=0
options snd_intel8x0 index=1
options saa7134-alsa index=2

Like the guy on the link I posted above said. But for some reason it still won't work.

---

