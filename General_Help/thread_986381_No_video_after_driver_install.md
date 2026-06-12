---
title: "No video after driver install"
date: 2008-11-18
forum: General Help
---

### Post by Tru7h on 2008-11-18
I installed the recommended driver for my 9600GSO video card and when I rebooted the Ubuntu splash screen was there but then it disappeared and the next thing I heard was the sound the login screen makes.  I hit the power button and rebooted again same thing.  Can someone please help me?
BTW: 8.10 64-bit
Driver version is 173
Recovery Mode DOESN'T fix the problem

---

### Post by Tru7h on 2008-11-18
Please help

---

### Post by Yellow Pasque on 2008-11-18
In recovery mode, try using envy to install the video driver:
```
sudo apt-get install envyng-core
```

---

### Post by Tru7h on 2008-11-18
I ran the code now what.

---

### Post by Tru7h on 2008-11-18
Please for the love of god could someone HELP ME!!!!!!!!

---

### Post by mcheshpants on 2008-11-19
when you hear the login screen come up log in and once you hear the  little drums or whatever when the desktop loads hit ctrl+alt+f3 to bring up the low res terminal which should be visible now then log in and try:

 "sudo dpkg-reconfigure xserver-xorg" 

it should re detect your computers video hardware

---

