---
title: "Wireless card"
date: 2009-03-14
forum: Hardware
---

### Post by Kinetic_lord on 2009-03-14
Where can i see what kind of wireless card i have?

---

### Post by evilgourmet on 2009-03-14
Hello,

A simple way you can find your wireless card is: 

From terminal ( from the menu: Applications > Accessories > Terminal ).
 ```
lspci | grep Network
```

It will give you the model of the card such as:

```
01:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

From there, you can load the drivers or determine what drivers you need.

---

### Post by Kinetic_lord on 2009-03-16
ok, thanks :)

---

