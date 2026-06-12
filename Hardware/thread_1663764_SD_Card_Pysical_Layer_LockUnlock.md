---
title: "SD Card Pysical Layer Lock/Unlock"
date: 2011-01-10
forum: Hardware
---

### Post by Vivek.Yarra on 2011-01-10
According to sd card physical layer specification an sd card can be locked providing a password, which later will be used for unlocking the card. The password and its size are kept in a 128-bit PWD and 8-bit PWD_LEN registers, respectively. These registers are non-volatile so that a power cycle will not erase them.

can someone help me how i can achieve this on ubuntu

Reference: 
section 4.3.7
[http://www.sdcard.org/developers/tech/sdcard/pls/Simplified_Physical_Layer_Spec.pdf](http://www.sdcard.org/developers/tech/sdcard/pls/Simplified_Physical_Layer_Spec.pdf)

Thank You

---

