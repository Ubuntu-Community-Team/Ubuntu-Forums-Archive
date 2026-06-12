---
title: "Determine memory, CPU etc"
date: 2008-11-04
forum: General Help
---

### Post by ka1eui on 2008-11-04
HI.
I have switched from Windows to Ubuntu and am very happy.  I would however like to be able to type in a command and see how much memory I have, both physical and vitual, type of processor, and other pertinent data.  Is there a command I can use to do that?
thanks
KA1EUI

---

### Post by iponeverything on 2008-11-04
Just add the "System Monitor" applet to your panel and click on it :)

(start off by right clicking on your panel)

---

### Post by anotherdisciple on 2008-11-04
Open an terminal and type

```
top
```

---

### Post by Ryadt on 2008-11-04
Install this application.```
sudo apt-get install hardinfo
```
It will show up in System > Administration.

---

### Post by Portmanteaufu on 2008-11-04
There are two files which contain (almost too much) information about your memory and your processor.

Typing
```
cat /proc/cpuinfo
```
will tell you everything you could possibly want to know about your processor.
Typing
```
cat /proc/meminfo
```
will tell you everything you could possibly want to know about your memory.

Hope that helps!

---

### Post by kerry_s on 2008-11-04
sudo apt-get install lshw-gtk
or if you don't need a gui
sudo apt-get install lshw

---

