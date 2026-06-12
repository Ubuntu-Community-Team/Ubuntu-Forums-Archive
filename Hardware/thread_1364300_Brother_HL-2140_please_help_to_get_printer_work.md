---
title: "Brother HL-2140 please help to get printer work"
date: 2009-12-25
forum: Hardware
---

### Post by mickeyjoe on 2009-12-25
I need someone to walk me through it step by step (baby steps please) to get this printer to work.  This is a printer my mother bought for her Ubuntu computer.  If not, I'm going to have to return it to the store and get a different printer.  The Samsung printer I have on my Ubuntu box, when I plugged it in, it just worked.

---

### Post by mickeyjoe on 2009-12-25
bump

---

### Post by barnaclebill18 on 2009-12-25
I got a HL-2140 about 2 months ago and it just worked on my Karmic.

---

### Post by HappyFeet on 2009-12-25
If you can't get it going, return it and buy an HP. 99% of all HP's are plug and play.

[Here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") is the Brother linux drivers.

---

### Post by kansasnoob on 2009-12-25
After a bit of reading and a bit of guessing try:

```
sudo apt-get install brother-cups-wrapper-common brother-cups-wrapper-laser brother-cups-wrapper-laser1
```

It would also help to know what version of Ubuntu you're running.

---

