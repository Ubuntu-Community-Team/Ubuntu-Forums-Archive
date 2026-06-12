---
title: "What after sudo make install?"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by Tiganjero on 2009-05-19
Hi! I haven't just started using Ubuntu, but I'm new to the source compiling way of installing Ubuntu open source programs. I tried to install a few programs (That are in tarballs) so far, and I do it this way:
```
cd /LOCATION_OF_INSTALLATION_FILES/
./configure
make
make check (sometimes)
sudo make install
make clean
make distclean
```
Every time it seems like it's done, and installed, but the program is not in Applications. What do I do after the process that I already mentioned?
Thanks in advance.

George.

---

### Post by barnex on 2009-05-19
Most gui programs can be installed with Apllications > Add/remove software. Those installed there will appear in your menu.

When you install a program from source, it often has to be started from the command line. When you have compiled, e.g., gnuplot, you will have to type gnuplot in a terminal to start it.

---

### Post by Tiganjero on 2009-05-19
Thanks for that info. Tho it was helpful it only worked on one of my programs. For example  installed crystalspace and I entered it in the terminal and it did not work. It only worked with alltray. My guess is that I'm not doing something right... :)

---

