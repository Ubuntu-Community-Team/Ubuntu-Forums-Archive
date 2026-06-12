---
title: "Keyboard not fully working"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by dp6ai on 2007-11-14
I am new to Ubuntu.

I have installed the latest version (7.10) and all was working fine after the install. Today when i started the Laptop i get to the login prompt but could not type certain keys.

I booted in to the live cd and opened a text editor to see what was going on and it appears that all my keys work except the whole of the qwerty row (minus t and y). That is i cant type QWERUIOP, but i can type TY[] etc.

My only login to the machine contains an i and a p. 

Does anyone know how to log in (with root maybe) and fix this issue?


thanks in advance.

dp

---

### Post by ajgreeny on 2007-11-14
Fit new keyboard, surely.  You can try logging in with an external keyboard to look into problems, but it sounds like a hardware problem and even using the recovery mode that is available at grub with your existing keyboard will not be simple, as you will still have a useless keyboard, and won't be able to type things needed in the recovery console mode.

---

### Post by bingoUV on 2007-11-14
Temporarily, to solve problems, use onscreen keyboard. System -> Preferences -> Accessibility -> Assistive Technology Preferences -> onscreen keyboard

Does it happen in text mode also (ctrl - alt - F1) ?   If yes, it is very likely a hardware problem. If not, post the output of 
```

xmodmap -pke

```

from within a terminal in the graphical session.

---

