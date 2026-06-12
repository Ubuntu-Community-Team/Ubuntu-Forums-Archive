---
title: "Fiesty makes no sound HELP!!!"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by nik62790 on 2007-10-24
I have a Toshiba satellite A135-S2356, 512MB ram, 80GB sata hd, Celeron M620 1.6GHz processor....not quite sure what the sound and video specs are and i cant get it to make any noise...Ive done all i can with my knowledge (which isnt very much) and now i really need help.

---

### Post by taurus on 2007-10-24
See what kind of sound card does it have by running this command from a terminal.

Applications -> Accessories -> Terminal
```
lspci
```
Then, look in System -> Preferences -> Sound -> Device: and see if it uses the soundcard on your laptop.

---

