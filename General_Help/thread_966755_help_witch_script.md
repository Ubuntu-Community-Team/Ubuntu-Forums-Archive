---
title: "help witch script"
date: 2008-11-01
forum: General Help
---

### Post by garmada` on 2008-11-01
I need create script to install about 100 deb package. I use aptonCD but apton only copy deb to system no install. Plz help.

---

### Post by RequinB4 on 2008-11-01
No script needed
```

sudo dpkg -i /home/a/specific/directory/*.deb

```

will install all of the .deb files in directory /home/a/specific/directory/

---

