---
title: "Speaker and headphones working together against me"
date: 2009-07-12
forum: Hardware
---

### Post by PsyMonkey on 2009-07-12
Hi,

I have a MS GT725-210UK laptop running Ubuntu 9.04 Jaunty Jackalope.

When I plug in my headphone the sound still plays via my laptop speakers.
```
psymonkey@psymonkey:~$ cat /proc/asound/card0/codec#* | grep Codec
```Gives the output
```
Codec: Realtek ALC1200
Codec: Motorola Si3054
```

Adjusting the volume of the front speaker adjusts the volume of the headphone and the speaker.

Anyone know the magic words to fix my issue?

---

