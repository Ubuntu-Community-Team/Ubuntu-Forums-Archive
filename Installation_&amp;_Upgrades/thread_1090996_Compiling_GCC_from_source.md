---
title: "Compiling GCC from source"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by Neo_The_User on 2009-03-08
I'm having trouble compiling GCC 4.4

[http://gcc.releasenotes.org/snapshots/LATEST-4.4/](http://gcc.releasenotes.org/snapshots/LATEST-4.4/)

I'm trying to compile a kernel with the latest bleeding edge version of GCC and it won't compile. I ran sudo apt-get build-dep gcc and I always get errors with ./configure so any help would be greatly appreciated.

---

### Post by Partyboi2 on 2009-03-09
What are the errors you are getting?

---

### Post by Neo_The_User on 2009-03-09
I'm currently running this Hard Drive nuker right now so I can't get you that info ATM. It's so funny the latest version of gcc came out on my birthday.

---

### Post by Neo_The_User on 2009-03-09
Works now I fixed the tool chain problem myself.

***SOLVED***

You can't just run build-dep gcc. You have to run build-dep gcc g++ libstdc++5 libstdc++6 and it works. This is why I love debian based distros. The build-dep command is just so handy at times like these. I am going to write a guide on compiling a kernel from source using gcc compiled from source when I am finished. It's going to be so fast when it's finished. Compiler flags for gcc and kernel set to i686! WOOO WHOOOO!!

---

