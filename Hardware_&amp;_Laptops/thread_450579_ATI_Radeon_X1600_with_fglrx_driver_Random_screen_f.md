---
title: "ATI Radeon X1600 with fglrx driver Random screen freeze"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by jackobize on 2007-05-21
I am using a AMD64 with ATI Radeon X1600Pro AGP video cards and my screen would randomly freeze on me.  Looking at the output of fglrxinfo and /var/log/xorg.log, it seems like the flgrx driver got loaded and configured properly for the Radeon X1600 PRO.  The issue is present either on ubuntu 6.10 or 7.04. Anyone using this video card without the random freeze ?

Thanks for the help

---

### Post by blazercist on 2007-05-21
i have the X1600 mobility on my laptop and it works fine, are you using the 64 bit feisty? perhaps its a 64 bit issue?

---

### Post by jackobize on 2007-05-21
Do you use fglrx, radeon or ati driver, and do you have any specific option enabled ? I will try to  install the i86 version of ubuntu 7.04 and see if it makes a difference. I have put back my old ATI Radeon 9250 and so far no freeze. This is why I thinking it is a support issue for the ATI X1600.

Thanks

---

### Post by blazercist on 2007-05-22
I use fglrx with no specific options, I even use beryl/xgl without any major problems.

---

### Post by butelo on 2007-05-25
same here. radeon x1600 and freezes when I load any opengl application i.e. if I run glxgears in a terminal.:(
I use a Feisty 32 and a  2.6.20-15-generic kernel

---

### Post by zambaroo on 2007-05-26
Take a look here: [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

-z

---

