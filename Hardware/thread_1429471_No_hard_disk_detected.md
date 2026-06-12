---
title: "No hard disk detected"
date: 2010-03-14
forum: Hardware
---

### Post by varungolechha on 2010-03-14
hi guys i have installed ubuntu 9.10 having windows xp too. ubuntu is not detecting mine drive d which there in xp....please help in this regards as soon as possible....i have all my data over in drive d and c drive is full so cant even shift the data.......... thanks..........

---

### Post by perham on 2010-03-14
> **varungolechha said:**
> hi guys i have installed ubuntu 9.10 having windows xp too. ubuntu is not detecting mine drive d which there in xp....please help in this regards as soon as possible....i have all my data over in drive d and c drive is full so cant even shift the data.......... thanks..........

have you tried mounting it? please post the output of ```
sudo fdisk -l
``` and ```
mount
``` and ```
cat /etc/fstab
```

---

