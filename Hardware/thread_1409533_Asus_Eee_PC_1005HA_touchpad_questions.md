---
title: "Asus Eee PC 1005HA touchpad questions"
date: 2010-02-17
forum: Hardware
---

### Post by Axess_Denied on 2010-02-17
Just a got a new Asus Eee PC netbook and I love it. Chose to dual boot with Xubuntu (Karmic) as it is less needy than UNR. Anyone familiar with getting two-finger scrolling to work in Xubuntu? All old posts point to options that deprecated at Jaunty. Thanks!

---

### Post by pi/roman on 2010-02-17
You can use this guide: [http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)
You just need to try it with synclient. Mine would be:
```
synclient verttwofingerscroll=1
```
Do the same for horiztwofingerscroll.
Then for karmic you should use hal to configure it permanently so go to section 4b for that.

---

### Post by pi/roman on 2010-02-20
Did this work?

---

