---
title: "Inspiron 4000 screen"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by NinjaTails on 2007-09-03
I recently got Ubuntu to run on my laptop, but I can't get my screen resolution past 800x600. (the native is 1024x768) does anybody know how to change this???

---

### Post by angryfirelord on 2007-09-03
Open a terminal & type:
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to where it says:
```
Section "Screen"
```
You should see something called *Modes*. They probably look like this:
```
Modes		 "800x600" "640x480"
```
Change all of them to say:
```
Modes		"1024x768" "800x600" "640x480"
```
Log out & log back in.

---

