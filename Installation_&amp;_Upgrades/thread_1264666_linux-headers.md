---
title: "linux-headers"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by chulengo on 2009-09-12
Hi I am not speak english! Im from argentina... sorry for the gramatical

I can't install linux-headers in ubuntu 9.04, I install all packages of linux-headers and try the command: apt-get install linux-headers(uname -r) and etc etc... 

I am installing enuwi-g2 driver and this is the erro:

make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-15-generic'


help! thank and good luck whit traduccion!

---

### Post by wojox on 2009-09-12
Did you sudo:

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Soul-Sing on 2009-09-12
```
sudo apt-get install linux-headers-`uname -r`
```

---

