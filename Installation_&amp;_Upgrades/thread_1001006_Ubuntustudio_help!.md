---
title: "Ubuntustudio help!"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by phlenix on 2008-12-03
Well i installed ubuntustudio on my dell laptop. well everything went well but when i started the laptop there was this black screen with the white text, looked like it was testing osmething, and then it told me to log in which i did. but instead of some desktop appearing there was plain text. it said my name and then some dollar sign and it wanted me to put some commands there. how can i start the OS????

---

### Post by MiD-AwE on 2008-12-03
It sounds strangely familiar. Maybe your xserver isn't configured properly? Have you tried to reconfigure x?
 
```
sudo dpkg -reconfigure xserver-xorg
```

---

### Post by phlenix on 2008-12-03
oh i got it it somehow forgot to install the actual os. in only installed the kernel lol

---

### Post by MiD-AwE on 2008-12-03
> **phlenix said:**
> oh i got it it somehow forgot to install the actual os. in only installed the kernel lol
 I'm glad to hear it's working for you.
;)

---

