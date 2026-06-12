---
title: "fgl"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by calyx on 2005-04-10
I have an ati card in my laptop but my fresh install of Ubuntu Hoary doesn't seem to be able to handle 3d properly (eg 3d screensavers) whereas Warty was perfect, I tried installing the xorg-driver-fglx package using apt and got:

sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fglrx

I can't find it in the synaptic gui either. Can anybody help?

---

### Post by humanity_to_others on 2005-04-10
I can find. Maybe you didn't enable all of your repsitories.

---

### Post by calyx on 2005-04-10
I just did a fresh automatic install, I don't remember any repositories options. Any idea how I can enable them?

---

### Post by humanity_to_others on 2005-04-10
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
```

---

### Post by node on 2005-04-10
```
sudo apt-get install synaptic
``` will get you synaptic anyway ;)

---

