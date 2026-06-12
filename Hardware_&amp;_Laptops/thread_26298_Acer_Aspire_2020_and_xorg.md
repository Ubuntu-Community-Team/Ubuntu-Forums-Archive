---
title: "Acer Aspire 2020 and xorg"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by DJ_Steve on 2005-04-12
Hi to everybody,



I have an "Acer Aspire 2020" with an "ATI 9700 mobility 128 MB" and I installed Ubuntu Linux 5.04 stable.  

I have a little problem with Xorg and 3D. 

The Ati drivers works but when I add the following lines in /etc/X11/xorg.conf



```
Section "Extensions"

       Option "Composite" "Enable"

EndSection
``` 



and I restart xorg the 3D effects turn off.



I find a little "how-to" ([http://ubuntuforums.org/archive/index.php/t-11477.html](http://ubuntuforums.org/archive/index.php/t-11477.html)) but it doesn't work.



Can you help me?



Thanks to all.

---

### Post by gbil on 2005-04-12
This is not a bug but a limitation of the driver so you can't do anything about it.

---

### Post by DJ_Steve on 2005-04-12
[QUOTE=gbil]This is not a bug but a limitation of the driver so you can't do anything about it.[/QUOTE]
 ok but the "how-to" is uncorrect! ;) becouse the autor write this: " If your using an ATI card add :

Option "backingstore" "true" "

Tnks :)

---

