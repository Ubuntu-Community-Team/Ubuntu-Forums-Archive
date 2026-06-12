---
title: "Touchpad stops working on Acer Chromebook 14"
date: 2020-05-27
forum: Hardware
---

### Post by adibudeen on 2020-05-27
I installed Ubuntu on my Acer Chromebook 14. Everything works except the touchpad will occasionally stop responding. The only workaround I've found to get it functioning again is:

```
sudo rmmod elan_i2c
sudo modprobe elan_i2c

``` 

Does anyone know of a permanent fix?

---

