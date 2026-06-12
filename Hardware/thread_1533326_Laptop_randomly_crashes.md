---
title: "Laptop randomly crashes"
date: 2010-07-17
forum: Hardware
---

### Post by billyss on 2010-07-17
Hello, I have been experiencing this problem for a couple of weeks now. While I'm using my laptop, out of nowhere, colorful lines appear on the screen and bang; everything turns off. This is the first time it happens on pc... I can't figure out what's wrong. It runs smoothly until this ramdom crash. Sometimes it will crash in an hour and sometimes in like 4 hours. 

If you have any idea what can it be (or if it's related with the OS), help would be much appreciated.

---

### Post by quixote on 2010-07-19
Colorful lines on the screen followed by crashing could be that the graphics driver you're using isn't really right for your card or chipset.  It's good enough to boot, but not good enough to be stable.  What's your make and model of computer?  Which version of ubuntu are you running?  And what's your graphics card?  You can find out the latter by opening a terminal (Applications > Accessories > Terminal) and typing ```
 lspci | grep 'VGA'
```

---

