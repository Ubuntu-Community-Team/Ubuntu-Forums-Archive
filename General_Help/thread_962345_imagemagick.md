---
title: "imagemagick"
date: 2008-10-29
forum: General Help
---

### Post by reesy on 2008-10-29
I have Ubuntu - Gutsy Gibbon installed. I am attempting to install startup manager in the synaptic package manager but it keeps giving me this error message

nautilus-image-converter:
 Depends: imagemagick  but it is not installable

If any one could tell me how to fix the problem that would be great thanks.

---

### Post by lucasl on 2008-10-29
Try clicking reload in the top left corner of Synaptic and try again. Also try searching for imagemagick and see if it comes up.

---

### Post by bapoumba on 2008-10-29
imagemagick has dependencies in the universe repositories. Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

