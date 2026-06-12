---
title: "exit shell script"
date: 2008-07-18
forum: General Help
---

### Post by xoger on 2008-07-18
hi i've written a shell script that opens and closes the CD drives on a loop but i wont to be able to break the loop by pressing f12, any ideas

```
while true;
do
eject /dev/scd0
eject /dev/scd1
eject -t /dev/scd1
eject -t /dev/scd0
done
```

---

### Post by dcstar on 2008-07-18
> **xoger said:**
> hi i've written a shell script that opens and closes the CD drives on a loop but i wont to be able to break the loop by pressing f12, any ideas

```
while true;
do
eject /dev/scd0
eject /dev/scd1
eject -t /dev/scd1
eject -t /dev/scd0
done
```

Why do you think that F12 exits? CTRL-C will stop it, no doubt there are other ways to also do it.

---

### Post by schauerlich on 2008-07-18
Also, why do you need to constantly open and close the CD drives?

---

### Post by xoger on 2008-07-18
there are twelve function keys
and control c will only work if i load it in the terminal

I'm trying to use my computer as a musical instrument

---

