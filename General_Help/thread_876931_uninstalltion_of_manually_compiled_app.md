---
title: "uninstalltion of manually compiled app?"
date: 2008-08-01
forum: General Help
---

### Post by StOoZ on 2008-08-01
Ok , assuming I install a program from a source (configure...make...make install etc)
if  I want to uninstall it , I need to have its installation , to do make uninstall (right?) , is there any better way than this?

since , I dont want to keep all the installation files, its just consumes space ,and has nothing useful except from when I want to uninstall stuff..

---

### Post by Choad on 2008-08-01
if you use a program called checkinstall (configure, make, checkinstall), it installs it using the apt system and asks you to give it a name so you can uninstall it by typing sudo apt-get remove <package name>

other than that, i do not know

---

### Post by StOoZ on 2008-08-01
so instead of doing :
./configure
make
make install

I should install that program and do it like :
./configure
make
checkinstall

??
and this program knows what software do I want to install?

---

### Post by soxs on 2008-08-01
> **StOoZ said:**
> so instead of doing :
./configure
make
make install

I should install that program and do it like :
./configure
make
checkinstall

??
and this program knows what software do I want to install?

well, in general I prefer
```
./configure
sudo make
sudo checkinstall --fstrans=no
``` since checkinstall had a nasty bug when using fdtrans without that switch(I often got build-pkg errors).

Edit: use ```
sudo apt-get install to install checkinstall
```

---

### Post by unoodles on 2008-08-01
Heres what to do, go back to the source and type:
sudo make uninstall
this will uninstall the program that you have compiled from source.

What Choad is trying to say is that if you install the program checkinstall (sudo atp-get install checkinstall), then when you compile a program, instead of typing sudo make install, you type sudo checkinstall, this will create a .deb file which you can double click and then uninstall from synaptic.

---

### Post by geirha on 2008-08-01
> **StOoZ said:**
> so instead of doing :
./configure
make
make install

I should install that program and do it like :
./configure
make
checkinstall

??
and this program knows what software do I want to install?

No, it runs make install for you and keeps track of all files it installs, those are then added to a new .deb-package (which you can name to your choosing. Obviously naming it the same name as the program you installed would be the logical thing to do). When you wish to uninstall, you remove that package. 

unoodles mentions that you can do sudo make uninstall. That is true for a lot of packages, but not all. Some developers use different build systems, and they may not include an uninstall target, or even use make at all.

```

./configure
make
sudo checkinstall

```

---

