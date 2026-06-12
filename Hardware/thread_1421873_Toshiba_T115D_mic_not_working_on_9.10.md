---
title: "Toshiba T115D mic not working on 9.10"
date: 2010-03-04
forum: Hardware
---

### Post by acron1 on 2010-03-04
I installed 9.10 on my Toshiba T115D-S1125 and it was a smooth install. Everything seems to work including the web cam and sound but the mic is not...

[IMG][IMG]http://i50.tinypic.com/2a8kpye.png[/IMG][/IMG]

[IMG][IMG]http://i48.tinypic.com/11abzoo.jpg[/IMG][/IMG]

[IMG][IMG]http://i50.tinypic.com/2nr0v80.png[/IMG][/IMG]

I have maxed everything out in alsamixer and still nothing...
Any help would be greatly appreciated...

---

### Post by acron1 on 2010-03-05
No one has a clue on this one???

---

### Post by acron1 on 2010-03-07
...is there anybody out there?...

---

### Post by acron1 on 2010-06-02
For anyone interested, this worked for me:

Add the following to /etc/modprobe.d/alsa-base.conf

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

---

