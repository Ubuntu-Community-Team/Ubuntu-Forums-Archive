---
title: "USB Mouse, six buttons"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by malfist on 2007-08-24
I know how to get a five button mouse working. Edit xorg.conf to show buttons 5 6, test them en xev and map them using xmodmap. But that doesn't seem to be working for my 6 button mouse. I tried editing xorg.conf to do 5 6 7 8 but that didn't work. Xev showed my wheel as being 4 (up) 5 (down) 2(click) Left click was 1, and right click was 3. but the extra buttons were 1 and 3 and one didn't show anything.
I changed my xorg.conf back to just 4 5 (so I could scroll with my wheel) and tested again with xev, the extra buttons still reported 1 and 3 and the other still didn't work (and it's the one I want to work most :( , gah).

Anyone know how to fix this? I 've been using xev like this:
```

xev | grep button

```
Because there's just too much output otherwise.

---

### Post by linuxwizard on 2007-08-24
Look over this might be something that will help you

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by malfist on 2007-08-25
no, that really didn't help :(

---

