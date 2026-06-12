---
title: "problem with ./configure and c"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by lolium on 2009-07-29
I am Currently trying to install HBasic but when i try compile the source code it gives me a c error

Here is what i type in terminal

```
lolium@lolium-desktop:~/Desktop/HBasic-2007-2a$ ./configure

```
This is the error I received
```

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```
And i can't work out the problem from the config log

How do i get this to compile properly??

Cheers

Lolium

---

### Post by Partyboi2 on 2009-07-30
Hi, have you got the 'build-essential' package installed? If you have not got it installed you can install it from the terminal with
```
sudo apt-get install build-essential
```

---

