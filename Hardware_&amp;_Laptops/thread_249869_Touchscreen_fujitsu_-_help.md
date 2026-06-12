---
title: "Touchscreen fujitsu - help"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by dadoprom on 2006-09-03
Hello, I am a happy user of a Ubuntu linux dapper drake, but unfortunetly not all of my hardware works. I am especialy talking about my fujitsu touchscreen. Once I found drivers for this panel [here]("http://www.conan.de/lifebook/lifebook.html"), and they worked  beautifely. But it was with the Xorg 6.8.x (in 3 different distros). I believe Ubuntu runs with xorg 7.0 thus what should I do? Is it possible to downgrade, will my wacom graphire 4 work, if downgraded (it works now)? I have installed this "X.Org X server -- FPIT input driver
This package provides the driver for Fujitsu Stylistic tablet PCs", but I dont know how to configure in xorg.conf, isnt it  even for active touchscreens?
I use i810 drivers for my intel graphic card. Newest kernel from ubuntu.

thanx for any suggestion

I hope it is clear enough.

David

---

### Post by dadoprom on 2006-09-03
bummer

---

### Post by dadoprom on 2006-09-04
Help

---

### Post by dadoprom on 2006-09-04
so many experts and none of you can help?!

---

### Post by blackened on 2006-09-04
This isn't very common hardware. Give your request some time and someone is bound to respond. Yes it's possible to downgrade X.org:
Download the 6.8.x package you want to install and do
```
sudo dpkg --force-downgrade *packagename*
```

Sorry I couldn't be more help.

---

### Post by dadoprom on 2006-09-11
> **blackened said:**
> This isn't very common hardware. Give your request some time and someone is bound to respond. Yes it's possible to downgrade X.org:
Download the 6.8.x package you want to install and do
```
sudo dpkg --force-downgrade *packagename*
```

Sorry I couldn't be more help.

where can I download it?

---

