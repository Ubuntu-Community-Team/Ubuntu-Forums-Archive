---
title: "help with Envy"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by pixelhog on 2008-03-16
Hi everyone,
I recently installed ubuntu gutsy alongside XP (on an HP dv9000z laptop) and I absolutely love it!
Just one driver issue though...
My nvidia geforce 7600 go  card  refuses to enable when i try to enable it in the restricted drivers area.
I've done a ton of research on this before posting and I think my answer rests with using Envy.  However when  i double click on the package file for envy, it refuses to give me the option to install saying :  "Error: Dependency is not satisfiable: debhelper"
I tried enabling all of my repositories but that didn't help..

I provided a screenshot to show you my problem
If  anyone know another method to getting my graphics driver to work on my laptop model please let me know.
I greatly appreciate any helpful tips!
-steve

Edit*  actually, make that *two* driver issues...my wireless internet card doesn't work either :(

---

### Post by Nepherte on 2008-03-16
Try this in the console
```
sudo apt-get -f install
```
This should resolve your dependencies problems.

---

### Post by pixelhog on 2008-03-16
But my wireless internet card isn't working...  :(
apt-get uses internet, right?
is there some sort a downloadable package that i can install offline via a flash drive?

---

