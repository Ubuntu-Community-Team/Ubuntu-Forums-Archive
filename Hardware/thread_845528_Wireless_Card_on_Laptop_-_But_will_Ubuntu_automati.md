---
title: "Wireless Card on Laptop - But will Ubuntu automatically find it?"
date: 2008-06-30
forum: Hardware
---

### Post by calvinps on 2008-06-30
Hello again...

I might install Ubuntu tomorrow but I have a couple of questions:

(1) I have a Wi-Fi card installed on my laptop but will Ubuntu
    automatically detect it during installation?

(2) My laptop is widescreen, so what resolution is required?


Whoever can answer those questions, thank you in advance.

---

### Post by sdennie on 2008-06-30
1) It depends on the wifi card.  I'm not sure how to figure this out in Windows but, if it's an Intel wifi card, it will work without any configuration on Ubuntu.

2) It should set the resolution properly without any problems.

The easiest way to test both of these things would be to simply download and burn an Ubuntu LiveCD and boot from it.  That should show you the level of compatibility for your hardware without having to install Ubuntu.

---

### Post by calvinps on 2008-07-01
I think it's an Atheros wireless card. I will probably need to scurry for those wi-fi drivers.

---

### Post by calvinps on 2008-07-04
I cannot connect to the internet on my laptop since I installed Ubuntu. I think it needs the following drivers...

Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 wireless LAN cards.

Where can I find those drivers?

---

### Post by sergiom99 on 2008-07-04
please post the output of 
```
 sudo lspci
```

---

