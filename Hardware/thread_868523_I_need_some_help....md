---
title: "I need some help..."
date: 2008-07-23
forum: Hardware
---

### Post by Prominence on 2008-07-23
I have two things that aren't working right and I was wondering if you guys could help me out with it.

Atheros Hard Access Layer (HAL)
Support for Atheros 802.11 wireless LAN cards

---

### Post by Dark_Stang on 2008-07-24
Post the output of "lspci" so we can see what type of wireless card you have.

---

### Post by Prominence on 2008-07-24
How do I do that?

---

### Post by ibutho on 2008-07-24
> **Prominence said:**
> How do I do that?

Run Applications -> Accessories -> Terminal and enter
```
sudo lspci | grep -i net
```
and also
```
sudo lshw -C network
```

---

