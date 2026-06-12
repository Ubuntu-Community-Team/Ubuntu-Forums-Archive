---
title: "USB TV Tuner - how to"
date: 2012-06-09
forum: Hardware
---

### Post by szrejciu366 on 2012-06-09
Hello,
I've got a USB TV Tuner Omega T900 and I've encountered problem. On the attached CD are only drivers for Windows. Does anyone know how to make it works on Ubuntu 12.04 (64-bit version)?
Please respond quickly.

---

### Post by howefield on 2012-06-09
Is the tuner being recognised, try..

```
dmesg | grep -i dvb
```

And have you checked for drivers via Additional Drivers ?

---

### Post by wyliecoyoteuk on 2012-06-09
Also try 

```
lsusb
```

Appears that it uses this decoder:
ITE_IT9135

You probably need to copy the right firmware to  /lib/firmware

Look here 
[http://linuxtv.org/wiki/index.php/ITE_IT9135](http://linuxtv.org/wiki/index.php/ITE_IT9135)

---

### Post by szrejciu366 on 2012-06-10
Thanks a lot! :KS

---

