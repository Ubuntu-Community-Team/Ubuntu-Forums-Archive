---
title: "fingerprint reader problem"
date: 2009-03-01
forum: Hardware
---

### Post by pdcox on 2009-03-01
i have a toshiba satelite a205-s4777 and installed ubuntu, everything works perfectely execpt for the fingerprint reader.
anyone know how can i solve it?

---

### Post by K. Hendrik on 2009-03-02
hi,
could you please post the result of ```
lsusb
```

---

### Post by pdcox on 2009-03-02
```
Bus 002 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

```

---

### Post by K. Hendrik on 2009-03-02
I think your device should be compatible ([here]("http://reactivated.net/fprint/wiki/Upekts")) did you install fprint already?

---

### Post by pdcox on 2009-03-02
i will have a look and will post the feedback, thanks for the post

---

### Post by K. Hendrik on 2009-03-02
no problem
and if you don't have fprint installed it's in the repos just
```

sudo apt-get install fprint-demo libfprint-dev libfprint0 libpam-fprint

```
then try fprint-demo

---

### Post by pdcox on 2009-03-02
fprint-demo is installed and working fine, but now how do i use it to log on in ubuntu ?

---

### Post by K. Hendrik on 2009-03-03
in this [HowTo]("http://ubuntuforums.org/showthread.php?t=760018&highlight=fprint") it's explained start reading at Step 4.

---

