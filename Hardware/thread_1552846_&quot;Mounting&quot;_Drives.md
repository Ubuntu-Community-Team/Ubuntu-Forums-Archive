---
title: "&quot;Mounting&quot; Drives"
date: 2010-08-14
forum: Hardware
---

### Post by ranga_97 on 2010-08-14
In DSL, what does this mean?
What do I have to do?
And does this mean that every time that I insert a floppy disc or CD, I have to mount and unmount?


One More thing, if I have to do it every time, what's the easiest way to it?

---

### Post by cj13579 on 2010-08-14
If you want to have a drive automatically mounted at boot you need to edit your fstab:

```
gksu gedit /etc/fstab
```

For more information on fstab take a look [here]("https://help.ubuntu.com/community/Fstab").

---

### Post by IcarusR on 2010-08-14
CDs should mount automatically upon insertion. Not sure about floppies, not used one for years !!

> In DSL, what does this mean?

Not sure what you mean by this, can you be more specific ?

---

### Post by ranga_97 on 2010-08-14
I'll try what cj said with the floppy drive and if the CD doesn't automatically do it, I'll do it to that as well. 

By doing this, does that mean you don't need a driver?

---

