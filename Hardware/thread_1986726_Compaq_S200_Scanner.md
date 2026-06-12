---
title: "Compaq S200 Scanner"
date: 2012-05-25
forum: Hardware
---

### Post by balasankarc on 2012-05-25
Hi all,
How can i make a Compaq s200 scanner to work on ubuntu 12.04??? the drivers are available only for windows xp...

Pls help me

---

### Post by ajgreeny on 2012-05-25
Have you tried using **simple-scan** or **xsane** yet; you may find that the scanner works already.

You can also try the terminal command ```
*sane*-*find*-*scanner
```*

---

### Post by balasankarc on 2012-05-25
> **ajgreeny said:**
> Have you tried using **simple-scan** or **xsane** yet; you may find that the scanner works already.

You can also try the terminal command ```
*sane*-*find*-*scanner
```*

Yup...i did it...but no scanners found... 
when i try lsusb in terminal, the scanner is shown in the list..
i tried using windows xp in virtualbox...but it is not even detecting the scanner...

pls help!!!

---

### Post by balasankarc on 2012-06-11
Ah... i used vmware player and installed windows xp in it... it detected my scanner...
thnks 2 all 4 helping...

---

