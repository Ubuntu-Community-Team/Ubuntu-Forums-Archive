---
title: "Lenovo T61 Driver help"
date: 2009-05-24
forum: Hardware
---

### Post by EricKnieriem on 2009-05-24
My problem originated when I tried to install AWN onto my newly installed Linux run Lenovo T61.

I have followed all of the appropriate steps to the installation. However I continue to receive the error message : 

"Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

I have installed compiz fusion and ran it. I believe my problem lies in the fact that I have not installed my video drivers yet. I would do this except that I dont know how. I have tried to follow through the System>Administration>Hardware Drivers Path. But yet It wont find any.

Any help?

---

### Post by EricKnieriem on 2009-05-25
bump.

Come on anyone?

---

### Post by luks911 on 2009-05-25
Please, run the lspci command in a terminal:
```
lspci 
```
and paste the result here to see what video card yow have. Maybe it's one of the Intel with known problems for running compiz. You can find more information about this issue and many possible solutions searching in the forum and in the web.

---

