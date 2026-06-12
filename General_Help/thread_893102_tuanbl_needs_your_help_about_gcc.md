---
title: "tuanbl needs your help about gcc"
date: 2008-08-17
forum: General Help
---

### Post by tuanbl on 2008-08-17
Help me!
I want to install otcl-1.13 but I receive this message:


tuan@NQT:~$ cd /home/tuan/otcl-1.13
tuan@NQT:~/otcl-1.13$ ./configure
No .configure file found in current directory
Continuing with default options...
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
tuan@NQT:~/otcl-1.13$

---

### Post by Ahadiel on 2008-08-17
sudo apt-get install build-essential

---

