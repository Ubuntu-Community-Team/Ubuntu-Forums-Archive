---
title: "Missing xorg.conf"
date: 2010-06-17
forum: Hardware
---

### Post by rtobyr on 2010-06-17
On previous versions of Ubuntu, I could often save a lot of RAM on older computers by specifying vesa in the xorg.conf. On 10.04 there is no /etc/X11/xorg.conf. Where can I specify what video driver I want Lucid to use?

---

### Post by howefield on 2010-06-17
Make one.

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by oneloveamaru on 2010-06-17
They did away with xorg.conf because Xorg is supposed to be able to detect everything automatically.. which we know isn't always what happens..

so yes, just create it like howefield said and it'll use it.

---

