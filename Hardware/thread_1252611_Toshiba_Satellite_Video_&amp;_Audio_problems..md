---
title: "Toshiba Satellite Video &amp; Audio problems."
date: 2009-08-29
forum: Hardware
---

### Post by squeakyneb on 2009-08-29
I purchased a Toshiba Satellite L500 with ATi Radeon HD4650 graphics. Ubuntu doesn't seem to recognise the graphics card and is unable to play sound.

lspci returns this:
```
ben@ben-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:9480]
```

Does anyone know what could be causing this and/or how I can fix either of these problems.

Thanks,
Benny

update:
I also found this from lspci
```
01:00.1 Audio device: ATI Technologies Inc Unknown device aa38

```
Ubuntu doesn't seem to like my hardware :(

---

### Post by squeakyneb on 2009-08-30
Bumpity bump, someone must have an idea!

---

