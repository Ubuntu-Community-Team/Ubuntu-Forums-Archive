---
title: "My keyboard does not work properly"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by Tahir on 2007-03-03
I installed ubuntu and my (USB) keyboard worked but the caps lock key on it didn't.  My fix was this:

- open /etc/X11/xorg.conf 

- go to the line  

```
Option		"XkbLayout"	"uk"
```

and replace it with this:

```
Option		"XkbLayout"	"gb"
```

and it is thus fixed!!!

---

