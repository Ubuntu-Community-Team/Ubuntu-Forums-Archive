---
title: "smartdimmer - init_nvclock failed"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by dartakaum on 2005-12-08
Everytime i use smartdimmer to control my vaio britghtness oi get that error.

any ideia?

i've installed nvlock too..

---

### Post by firehead on 2006-01-14
hi dartakaum
i had the same problem after having installed smartdimmer via apt-get. now i installed it manually:
> 
$ wget [http://www.acc.umu.se/~erikw/program/smartdimmer-0.1.tar.bz2](http://www.acc.umu.se/~erikw/program/smartdimmer-0.1.tar.bz2)
$ tar xfvj smartdimmer-0.1.tar.bz2
$ cd smartdimmer/
$ ./configure && make && sudo make install
and it works now flawless, i didn't even install nvclock.
maybe it's because i'm using the newest NVIDIA-Driver... see this thread
[http://ubuntuforums.org/showthread.php?t=75074&highlight=NVIDIA](http://ubuntuforums.org/showthread.php?t=75074&highlight=NVIDIA)
for e detailed HOWTO on installing NVIDIA drivers, especially the posts 657-662...worked perfectly for me on a vaio s4xp...
good luck

---

