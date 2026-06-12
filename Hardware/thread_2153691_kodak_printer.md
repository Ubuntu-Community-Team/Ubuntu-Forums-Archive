---
title: "kodak printer"
date: 2013-06-12
forum: Hardware
---

### Post by zips12 on 2013-06-12
jusy installed  ubuntu am trying to install kodak printer unbuntu will not run install disk what am I doing wrong

---

### Post by Cheesemill on 2013-06-12
That install disc is made for Windows, it won't work with Ubuntu.

Can you give us more details please, which version of Ubuntu are you using and what is the model number of your printer.

---

### Post by paulnewall on 2013-06-12
if you have a recent ubuntu and a kodak aio printer, it should just work.
Use a printer setup tool to create a quese for the printer.
in my case , xubuntu 13.04, it's "settings manager", "printers"
add a printer and select your model from the lists presented
Then you can probably print

---

### Post by paulnewall on 2013-06-12
sorry, I meant queue for the printer, not quese

---

### Post by zips12 on 2013-06-13
11.04 in the proses of upgrading to 11.10 11.04 no longer supported maybe the reason ubuntu could not find drivers ?

---

### Post by paulnewall on 2013-06-14
I think ubuntu 12.04 was the first version with the c2esp driver included.
If you stay with 11.10, you could install the package c2esp_25c-1 using the deb file here
[http://sourceforge.net/projects/cupsdriverkodak/files/?source=navbar](http://sourceforge.net/projects/cupsdriverkodak/files/?source=navbar)

---

### Post by mörgæs on 2013-06-15
I would (as always) recommend a fresh install of 13.04, especially when hardware support is the problem.

---

### Post by kurt18947 on 2013-06-15
> **mörgæs said:**
> I would (as always) recommend a fresh install of 13.04, especially when hardware support is the problem.

I've debated this with myself.  Do I recommend a distro with such a short support cycle?  If the in-place upgrades work as promised it wouldn't be an issue but in-place upgrades have historically had a 'checkered' history.

---

