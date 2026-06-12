---
title: "overclocking ati vid card.."
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-10-08
Looking for some good software like atitool (windows) to overclock my card..
I have trid rovclock, but cant get it installed..
wont ./configure at all, i did a make but still nothing.. and no make install wont work either..
Is ther another ootion?
Thnax

---

### Post by floyd27 on 2005-10-08
roderick@ubuntu:~/Desktop$ tar jxvf rovclock-0.6b.tar.bz2
rovclock-0.6b/
rovclock-0.6b/COPYING
rovclock-0.6b/Makefile
rovclock-0.6b/README
rovclock-0.6b/pci.h
rovclock-0.6b/radeon.h
rovclock-0.6b/rovclock.c
rovclock-0.6b/ChangeLog
roderick@ubuntu:~/Desktop$ cd /home/roderick/Desktop/rovclock-0.6b
roderick@ubuntu:~/Desktop/rovclock-0.6b$ ./configure
bash: ./configure: No such file or directory
roderick@ubuntu:~/Desktop/rovclock-0.6b$ sudo ./configure
Password:
sudo: ./configure: command not found
roderick@ubuntu:~/Desktop/rovclock-0.6b$ sudo make
gcc -O2 -Wall -Wstrict-prototypes  -o rovclock rovclock.c
roderick@ubuntu:~/Desktop/rovclock-0.6b$ sudo make install
make: *** No rule to make target `install'.  Stop.
roderick@ubuntu:~/Desktop/rovclock-0.6b$

---

