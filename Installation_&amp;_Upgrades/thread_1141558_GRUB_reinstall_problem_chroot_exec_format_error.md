---
title: "GRUB reinstall problem/ chroot exec format error"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by supererki on 2009-04-28
Hello. 
so i messed up GRUB again, but i was not able to recover it this time. i booted from live cd 8.04, tried to reinstall grub but it said cannot mount your partition, couldnt find stage1 etcetc... so i mounted my root partition to /mount/root and i mounted proc to that folder and -o bind /dev etc . and then i did chroot /mount/root /bin/bash it said something like : 
cannot execute /bin/bash: Exec format error ...
what can i do ?
i have 64bit machine but installer is for 32bit. may this be problem ? should i try with newer installer like 9.04?
anybody?
thanks
erki

---

### Post by supererki on 2009-04-28
anybody?

---

