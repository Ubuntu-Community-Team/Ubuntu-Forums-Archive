---
title: "[SOLVED] Hardware Diagnostics???"
date: 2008-07-03
forum: Hardware
---

### Post by Stoppelmonster on 2008-07-03
Ok, the Linux-Nub back again, is there a way, program, code, tool, etc;.. I can utilize that would display to me the hardware installed/attached to my computer, including make/model etc;...  ??????

I would love for there to be.

Get back at me.

---

### Post by milosz.galazka on 2008-07-03
for example:
```
sudo lshw
```

Added:
Also there is *lshw-gtk* package for nice frontend, *dmidecode* tool and of course you could look into */proc* filesystem.

---

### Post by Stoppelmonster on 2008-07-03
Oh, wow, that is a fantastic command. Very detailed output. Very much thanks.

---

