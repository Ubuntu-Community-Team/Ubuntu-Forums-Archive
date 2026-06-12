---
title: "help me fix this"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by kamalkhadka on 2009-03-08
Hi, I am very new to Ubuntu. 
to run the flash i did the following in the terminal

sudo apt-get install ubuntu-restricted-extras

then a blue screen was shown i tried to agree it but it wasn't possible to click ok button.

then i went to synaptic package manager and the it showed the following thing. can any one help me fix this or show me any links where i can get help.

---

### Post by taurus on 2009-03-08
Close synaptic.  Then, open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
The blue screen that you've described is probably java licensing screen.  You need to hit the Tab key to highlight the <OK> and then Return to accept it.

---

### Post by kamalkhadka on 2009-03-08
thank you taurus.

two of those codes worked but the third one didn't

screen shot is below..

and sorry i am not very good at explaining the problems

---

### Post by taurus on 2009-03-08
```
sudo apt-get -f install
```

---

