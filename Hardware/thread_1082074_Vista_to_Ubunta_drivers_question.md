---
title: "Vista to Ubunta drivers question"
date: 2009-02-27
forum: Hardware
---

### Post by Masngr on 2009-02-27
Salut ,
I just siwtched from Vista to Ubuntu and now i have a question .
In Vista when i do format to my computer and install vista i need to download and install drivers from toshiba web site .
Now i switched to Ubuntu do i need to install drivers ?
And in toshiba they only put to my computer drivers these OS :
Windows vista 64
Windows Vista 
WIndows Xp
-=-
Should i install the vista drivers on my computer ?

-=
Thanks in Advance ):P

---

### Post by smani on 2009-02-27
One nice thing about linux is that you seldom have to care about drivers - they all get installed automatically with the kernel and other packages, and also updated automatically (if you update your system), therefore, no, you don't have to install any drivers, unless there are some devices that do not work, in which case you would have to search specifically for those drivers.

Just some general information about drivers: they are compiled for a specific operating system, they cannot be simply installed on another operating system for which they were not compiled. I.e. a dll or sys file such as the ones you find in windows drivers do not make any sense to the linux kernel. This is valid for any software in general: you have to specifically compile a program for a specific operating system to make it run.

---

