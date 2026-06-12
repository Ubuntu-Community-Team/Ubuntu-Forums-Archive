---
title: "incomplete install apturl"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by fusi.eon on 2009-06-23
i was installing apturl using this command in the terminal

"sudo apt-get install apturl"

all was well, when my net stopped working mid-way. since i'm new to linux, i've no clue what to do now. should i re-install it again using that command or is there any alternative command by which i can complete the incomplete install? 

thank you.

---

### Post by fusi.eon on 2009-06-24
anyone?

---

### Post by dsavi on 2009-06-24
Just try reinstalling it. Although I think that in the Ubuntu firefox modifications apturl is included. (Kubuntu has Firefox right? :P )

---

### Post by Achilles124 on 2009-06-24
Try it with adding -f to the terminal command.

-f standing for fixing broken packages.

For more information: man apt-get and look for -f

---

### Post by fusi.eon on 2009-06-24
thank you.

how do i uninstall an application? what command do i give? 

and if i want to know what all programs i've installed, what do i type in? 

thank you once again.

---

### Post by dsavi on 2009-06-24
```
sudo apt-get remove packagename
```
Where packagename is the name of the package (For example, gimp) you want to remove.

As for programs you've installed, that could be a problem as Ubuntu comes with well over a thousand programs (Or rather packages) installed.

---

### Post by fusi.eon on 2009-06-24
thank you.

---

