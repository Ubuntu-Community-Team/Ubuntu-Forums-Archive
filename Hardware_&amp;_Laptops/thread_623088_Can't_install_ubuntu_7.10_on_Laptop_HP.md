---
title: "Can't install ubuntu 7.10 on Laptop HP"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by residentevil on 2007-11-25
Hello, i have HP COMPAQ 6715S GR762ES, but I cant't install Ubuntu 7.10
It says that found screens, but no configuration or something close, please help me

---

### Post by Yellow Pasque on 2007-11-25
When you go to the terminal, run:
```
sudo update-pciids
sudo install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```

Restart the PC and let us know how it works.

---

### Post by residentevil on 2007-12-16
10x it is working !

---

