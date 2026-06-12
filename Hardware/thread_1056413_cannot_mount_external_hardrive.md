---
title: "cannot mount external hardrive"
date: 2009-01-31
forum: Hardware
---

### Post by wsamh on 2009-01-31
I have ubuntu 8.10 and I'm trying to mount an ide external hardrive, and I'm getting an "cannot mount device" error. does anyone know how to fix this.

---

### Post by taurus on 2009-01-31
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by Piro24 on 2009-01-31
What exactly are you doing?

Are you trying to  mount it from a graphical interface, or through a terminal?

Also, what FS is the EHD using?

---

