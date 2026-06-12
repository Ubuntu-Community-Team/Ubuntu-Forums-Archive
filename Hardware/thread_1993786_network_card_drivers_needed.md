---
title: "network card drivers needed"
date: 2012-06-02
forum: Hardware
---

### Post by Malachikhan122 on 2012-06-02
I installed ubuntu in a dual boot last night and can't get any drivers for the wireless network card make; *tenda* model; *twl541p* anywhere, is there a solution?
thanks

---

### Post by josephmills on 2012-06-02
can you plz open your terminal (ctrl+alt+t) and enter in
```
lspci -nn
```
```
rfkill list all 
```
```
lsmod
```

then paste that all here thanks.

---

### Post by Malachikhan122 on 2012-06-02
thanks for the advice but i got it working using ndiswrapper and finding the drivers using my windows install
> **josephmills said:**
> can you plz open your terminal (ctrl+alt+t) and enter in
```
lspci -nn
``````
rfkill list all 
``````
lsmod
```then paste that all here thanks.

---

