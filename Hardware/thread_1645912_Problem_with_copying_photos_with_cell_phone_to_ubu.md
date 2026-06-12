---
title: "Problem with copying photos with cell phone to ubuntu 10.10"
date: 2010-12-15
forum: Hardware
---

### Post by wlodarek1 on 2010-12-15
I have this problem.  In ubuntu 10.10 I can not copy photos from your phone via bluetooth. The devices are paired, they see each other. When I try to copy a picture to your phone displays the message, ERROR TRANSFER. I did not have that problem in earlier versions of ubuntu. My bluetooth device is; LogiLink - little finger .. Please help, why on ubuntu 10.10 normally, I can not copy photos from phone to computer?

---

### Post by cipherboy_loc on 2010-12-15
What type of phone is it? It could be that Ubuntu discontinued support (did you upgrade to 10.10, or did you do a fresh install?) for your type of phone.  Also, what type of bluetooh adapter doyou have? If it is built in, run:

```
lspci | grep -i 'bluetooth'
```

From a terminal (Applications -> Accessories -> Teminal).


Thanks,
Cipherboy

---

### Post by wlodarek1 on 2010-12-15
My ubuntu 10.10 is a fresh instalation.
My phone is a Samsung D900I 
```
darek@darek-G31M-S2L:~$ lspci | grep -i 'bluetooth'
darek@darek-G31M-S2L:~$ 

```
Not results .....
My bluetooth is a USB "dongle" device ;
> Bus 001 Device 009: ID 0e5e:6622 Conwise Technology Co., Ltd. CW6622

---

