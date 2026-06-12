---
title: "unique headphone speaker exclusivity problem?"
date: 2008-11-01
forum: Hardware
---

### Post by esmaeel on 2008-11-01
I'm relatively new to Ubuntu (it's been about 2 weeks now) and I've had 8.10 Intrepid installed since beta on my Lenovo Ideapad Y430. I have now found that I have what looks to me like a unique problem regarding my laptop's sound output. When I plug in headphones, only one of the speakers in my laptop turns off. I have read other guides on the forums for how to get the sound from the speakers to stop when I plug in headphones, but none of the solutions has worked for me. I am running a pulseaudio system as described here [http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio) .

typing head -n 1 /proc/asound/card0/codec* in terminal gives me the following:

==> /proc/asound/card0/codec#0 <==
Codec: Generic 8086 ID 2802

==> /proc/asound/card0/codec#2 <==
Codec: Conexant CX20561 (Hermosa)

---

### Post by esmaeel on 2008-11-02
can anyone help me?

---

### Post by esmaeel on 2008-11-08
help?

---

### Post by esmaeel on 2008-11-26
Actually, I realized that it is the subwoofer on the bottom right of my laptop that stays on when headphones are plugged in. I can't find any way to turn off or control the subwoofer. Any help will be truly appreciated.

---

