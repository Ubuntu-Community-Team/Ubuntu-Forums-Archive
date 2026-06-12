---
title: "Which video card do I have?"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by pjlmas on 2007-03-08
Hi, I'm trying to install [CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

but I don't know which video card do I have in my laptop. There's any command that could tell me this before I continue with the installation?

Regards.

---

### Post by teaker1s on 2007-03-10
try this

```
lspci | grep VGA
```

---

### Post by pjlmas on 2007-03-11
That is right, I have a

 plopez@plopez:~$ lspci | grep VGA

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GM L Express Graphics Controller (rev 03)

Thank you so much.

---

### Post by teaker1s on 2007-03-11
:popcorn: welcome

---

