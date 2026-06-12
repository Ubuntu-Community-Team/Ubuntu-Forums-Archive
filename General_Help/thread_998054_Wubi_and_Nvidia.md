---
title: "Wubi and Nvidia"
date: 2008-11-30
forum: General Help
---

### Post by Cubedout on 2008-11-30
hi im having a problem where after the Nvidia restricted drivers are enabled i get a problem booting

im presented with this after the load bar
```
[    2.183329] i8042.c: Can't read CTR while initializing i8042.
Loading, please wait...
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

Ubuntu 8.10 ubuntu tty1
```
and it then asks me to log in as u would in the terminal

ive been told this is a wubi issue.. if i canot get it to work from here.. how do i disable the driver from this command line

-cube

---

### Post by ago on 2008-12-01
This is not a wubi issue, it is a video driver problem, if you press esc at boot you can enter into rescue mode and usually fix things from there

---

