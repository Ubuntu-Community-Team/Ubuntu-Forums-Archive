---
title: "[SOLVED] resolution problem"
date: 2008-11-06
forum: General Help
---

### Post by karlmp on 2008-11-06
I did a fresh install of intrepid and everything seems ok except for the GDM login window

i get the upper-left corner

the resolution must be 1024x760

---

### Post by karlmp on 2008-11-07
This should work.

```
sudo gedit /etc/gdm/Init/Default
```

Go the end of the file and add this before the exit 0 line:

```
xrandr -s 1024x768
```

Now the resoultion of GDM will be 1024x768.

---

### Post by karlmp on 2008-11-13
thanks:)

---

### Post by Vunutus on 2008-11-13
Somewhat off topic but did you just ask a question, answer yourself, then thank yourself? :P

---

### Post by goggle5 on 2008-11-18
Your fix helped with my resolution problem at log-in but a couple of questions ... 

1). At log-in, the screen resolution is fine, BUT the font when you type in your user name/password is still set at the previous high resolution - any way to change that as well??

2). The font while Ubuntu boots up - when it shows the system checks and whatnot, is also at a at a high resolution ... anyway to fix this?


thx

---

### Post by karlmp on 2008-11-18
i don't know, I'm a noob too

check this:[http://ubuntuforums.org/showthread.php?t=981689](http://ubuntuforums.org/showthread.php?t=981689), look for post #7 and #8

here's documentation to edit xorg: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

if you're running hardy, type: 

```
sudo displayconfig-gtk
``` 

and set the resolution there

---

### Post by ricky15100 on 2008-12-10
you abolute bloody star karlmp worked a treat thanks bud):P

---

### Post by Trenchbroom on 2009-04-04
Had GDM menu resolution and this did the trick.  Thanks karlmp!

---

