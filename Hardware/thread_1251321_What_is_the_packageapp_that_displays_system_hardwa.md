---
title: "What is the package/app that displays system hardware in GNOME?"
date: 2009-08-27
forum: Hardware
---

### Post by lduperval on 2009-08-27
I just installed jaunty but I don't see the app that allows me to view the different hardware components.

Where do I find it? Anyone know its command-line name?

L

---

### Post by ajgreeny on 2009-08-27
```
sudo lshw -html > ~/hardware.html
```will produce a html file you can open in firefox (just double click) or you can install hwinfo or lshw-gtk if you prefer a gui

---

### Post by lduperval on 2009-08-27
Cool, thanks!

L

---

