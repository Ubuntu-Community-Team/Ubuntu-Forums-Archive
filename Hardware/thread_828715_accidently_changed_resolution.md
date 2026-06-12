---
title: "accidently changed resolution"
date: 2008-06-14
forum: Hardware
---

### Post by fbthpg on 2008-06-14
i accidently changed my resolution from 1280x800 to 1280x764

and dont look as good as they used to

is there a way i can reconfigure my graphics drivers, properties, etc... without having to track all my information down and reinstalling everything?

thanks in advance

---

### Post by overdrank on 2008-06-14
> **fbthpg said:**
> i accidently changed my resolution from 1280x800 to 1280x764

and dont look as good as they used to

is there a way i can reconfigure my graphics drivers, properties, etc... without having to track all my information down and reinstalling everything?

thanks in advance

HI and how did you change the resolution, by editing your xorg?

---

### Post by Rocket2DMn on 2008-06-14
You can reset your X settings by doing
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.

---

