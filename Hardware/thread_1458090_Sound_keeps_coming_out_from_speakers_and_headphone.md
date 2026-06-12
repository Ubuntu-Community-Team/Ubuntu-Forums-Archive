---
title: "Sound keeps coming out from speakers and headphones!"
date: 2010-04-19
forum: Hardware
---

### Post by _0R10N on 2010-04-19
Hi all!!

Last week I installed Karmic on my new laptop HP DV6. The first problem I've met, was not having sound at all. I solved the problem, but now I it keeps coming from the speaker even though the headphone are connected.

I followed some threads but nothing worked for me, so far. If someone solved it, please help.


Thanks in advance!

_0R10N >>

---

### Post by grege on 2010-04-19
A general suggestion.

Install gnome-alsamixer

This will give you many options for muting and un-muting different channels.

---

### Post by _0R10N on 2010-04-19
Thanks for replying. I'd already done that. It seems to be a problem related with high definition sound cards.:(

kind regards!

_0R10N >>

---

### Post by lidex on 2010-04-21
Saw your other posts. Try removing that line from your alsa-base.conf and replacing it with this one:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

And you will need to reboot for it to take effect.

---

### Post by _0R10N on 2010-04-21
Thanks!!! as soon as I get home I'll give it a try!:P

_0R10N >>

---

### Post by _0R10N on 2010-04-21
It works!!!! it workssssssssss!!!!!!!!!!! 

:lolflag:

Many thanks!!!


_0R10N >>

---

### Post by lidex on 2010-04-21
You're welcome. Enjoy!

---

