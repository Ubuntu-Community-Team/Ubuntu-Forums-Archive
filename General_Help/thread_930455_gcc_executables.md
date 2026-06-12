---
title: "gcc executables"
date: 2008-09-26
forum: General Help
---

### Post by hariskoul on 2008-09-26
Hallo,

     I am quite new to Ubuntu community. My actual problem is that I want to install some new programs like, emacs editor, but seems that I can't. That's because whenever I use the command ./configure the result is:

haris@ubuntu:~/downloads/emacs-22.3$ gcc ./configure
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
haris@ubuntu:~/downloads/emacs-22.3$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Therefor seems that gcc cannot create executables. How can resolve this ? How can install a new program anyway?

Thank you very much.

---

### Post by Pro-reason on 2008-09-26
What are you trying to install?  Emacs?  Delete everything you have downloaded and install it from Synaptic instead.

If you really need to compile some software from source, then install “build-essential”, and follow the instructions in the source-code tarball.

---

### Post by kdcoetzee on 2008-09-26
Try these two links.

[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")
[https://help.ubuntu.com/community/InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by hariskoul on 2008-09-26
Thank you about that , everything is working perfectly now.

---

