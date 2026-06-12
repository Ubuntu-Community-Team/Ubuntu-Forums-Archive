---
title: "change volume in shell"
date: 2008-07-18
forum: General Help
---

### Post by xoger on 2008-07-18
how do i change the volume in a shell script

---

### Post by pdwerryhouse on 2008-07-18
Use the *amixer* command, which is part of the *alsa-utils* package.

Some examples:

Fairly loud - 
```
amixer set Master front 20
```

Quiet -
```
amixer set Master front 10
```

Mute -
```
amixer set Master mute
```

Unmute -
```
amixer set Master unmute
```

In each of these cases, I've used the Master channel. You can get a listing of the available channels with:

```
amixer scontrols
```

---

### Post by sisco311 on 2008-07-18
i prefer alsamixer

---

### Post by xoger on 2008-07-19
thanks works great

---

