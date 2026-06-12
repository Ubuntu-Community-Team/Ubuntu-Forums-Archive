---
title: "Unzip PQRS.tgz to /opt/PQRS"
date: 2008-09-28
forum: General Help
---

### Post by kaysmart on 2008-09-28
[SIZE="4"]**How can i unzip PQRS.tgz to /opt/PQRS ? I tried with unzip option, but I faced permission problem**[/SIZE]

---

### Post by spiderbatdad on 2008-09-28
**sudo** unzip -d .../opt/don't/shout...

---

### Post by Elfy on 2008-09-28
You'll need to use sudo to unzip the file to /opt/PQRS , it needs root rights

```
sudo *command* file /path/
```

---

### Post by jespdj on 2008-09-28
The extention .tgz probably means that it's a gzipped tar file. You can unzip this with "tar xfz ...", for example:
```
cd /opt/PQRS
sudo tar xfz ~/PQRS.tgz
```

---

