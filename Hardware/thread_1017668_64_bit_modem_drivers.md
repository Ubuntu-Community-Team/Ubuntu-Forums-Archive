---
title: "64 bit modem drivers"
date: 2008-12-21
forum: Hardware
---

### Post by theozzlives on 2008-12-21
I have a Dell Inspiron 1525. I downloaded the Ubuntu drivers for my modem (hsfmodem_7.60.00.06oem_i386.deb). As you can see it's 32 bit, Dell don't provide 64 bit drivers (at least that I could see). My modem is a Conexant, D330, HDA, MDC, V92. I've thought about forcing install but it re-compiles the kernel and I don't wanna damage that. I also don't want to go to 32 bit just to use my modem. Any ideas???

---

### Post by xelxel on 2008-12-21
Depending on the reason for using 64bit OS, this is an option:

1. Install 32bit Ubuntu (This is assuming you are using 64bit in
order to access 4GB+ RAM)

2. run commandline, with following:
```
sudo apt-get install linux-image-server
```

That'll install the server edition of ubuntu with PAE support and that'll
let ubuntu 32bit find 4GB+ in RAM.

Then you should be able to install the 32bit modem drivers and still have all RAM accessible.

---

### Post by theozzlives on 2008-12-21
I only have 2 GB

---

