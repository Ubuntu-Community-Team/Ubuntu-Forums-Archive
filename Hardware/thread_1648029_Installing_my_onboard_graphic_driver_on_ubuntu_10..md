---
title: "Installing my onboard graphic driver on ubuntu 10.10"
date: 2010-12-18
forum: Hardware
---

### Post by Trueill on 2010-12-18
Hey,

I am trying to install my graphics driver but its in .run format.How do i execute it ? 

(I am an ubuntu newbie)

---

### Post by sikander3786 on 2010-12-18
Which graphics card is there?

Applications > Accessories > Terminal:

```
lspci | grep VGA
```

Instead of trying to install the .run package, go to System > Administration > Additional Drivers and activate the drivers there. That is the recommended way ;-)

---

### Post by Trueill on 2010-12-18
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

```And when i went to "Addional driver" i didnt see any driver to activate.

---

### Post by sikander3786 on 2010-12-18
Radeon X1200 is no longer supported under 10.10 I fear. You can have the open source drivers for that.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

