---
title: "Skype webcam fail, HP Pavilion g6"
date: 2012-08-08
forum: Hardware
---

### Post by ajukilibodin on 2012-08-08
Hello, I have an HP Pavilion g6 laptop. As soon as I turn the camera on during a Skype call, my system crashes and goes in to low-graphics mode. Any suggestions?

---

### Post by Vakman on 2012-08-08
Does your webcam work in other applications, say Cheese?

---

### Post by ajukilibodin on 2012-08-09
Yes it does. Cheese successfully records and takes photos.

---

### Post by Vakman on 2012-08-09
Open Terminal and try:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by ajukilibodin on 2012-08-11
It does work, and did work. But after about ~10 hours, it crashed again.

---

### Post by Vakman on 2012-08-12
> **ajukilibodin said:**
> It does work, and did work. But after about ~10 hours, it crashed again.

It was working and then after what it crashed?

Refer to here as well so you do not have to type that everytime
: [https://wiki.archlinux.org/index.php/Webcam_Setup#Get_software_to_use_your_webcam](https://wiki.archlinux.org/index.php/Webcam_Setup#Get_software_to_use_your_webcam)

---

