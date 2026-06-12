---
title: "X screen not displaying on HP Pavilion DV 4040us"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by knandyal on 2005-08-18
I am trying to install Ubuntu 5.04 on my laptop - HP Pavilion DV 4040us.  It has Centrino chipset, and uses Intel915 graphic chipset and the in-built  flatscreen is a LG philips make.


 After the install, the init levels come up OK, but when it switches to X, the screen goes blank (but the welcome tune is heard, meaning the X did come up OK, just that I can see it).   

The ctrl+alt+1 gives me a text based prompt and I am able to login in. 

The same happens when I boot from the Ubuntu Live CD too.

Any tips, as to how I can make it work?  All I know is that X comes up OK (sine I hear the welcome tune) but dont see it.   Also when I do a ps -ef, it shows X and its components running.

The lsmod shows that agpgart loaded, and the xorg.conf shows the i810 chipset. 

What am I doing wrong?

Any help is greatly appreciated, since I am planning to move to Ubuntu from Ms Windows.

Thanks
Karthik

---

### Post by ebossan on 2005-08-25
for my dell inspiron 2200, it seems i have the same problem.
in xorg.conf, i replace i810 by vesa and now it's ok
in root, change your xorg.conf and restart your kdm or gdm.
for now i don't know if there is another solution with i810

---

