---
title: "How can I join two files e.g: wmv.001 and wmv.002?"
date: 2008-10-24
forum: General Help
---

### Post by rado3105 on 2008-10-24
How can I join two files e.g: wmv.001 and wmv.002?

I was trying to do that running total commander under wine, but doesnt work.

---

### Post by cashmoney on 2008-10-24
```
cat wmv.00[1-2]>wmv.full
```

Cat means concatenate (combine files)
wmv.00[1-2] that is the files it will combine it will match wmv.001-wmv002

The output file will be wmv.full

---

### Post by kpkeerthi on 2008-10-24
Use avidemux

(I'm doubtful if you could cat 'video' files like that. It might corrupt the headers and meta data in the files)

---

### Post by Olav on 2008-10-24
[http://lxsplit.sourceforge.net/](http://lxsplit.sourceforge.net/)

---

### Post by ww711 on 2008-10-24
> **cashmoney said:**
> ```
cat wmv.00[1-2]>wmv.full
```

cat means concatenate (combine files)
wmv.00[1-2] that is the files it will combine it will match wmv.001-wmv002

the output file will be wmv.full

+1

---

### Post by meozeren on 2008-12-12
Thanks to cashmoney.

---

