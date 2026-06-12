---
title: "how to install wine 1.0.1.tar.bz2"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by icejack_outlaw on 2009-02-15
hi all, im newbee in ubuntu and installing ubuntu 8.04(Hardy) i have download wine 1.0.1.tar.bz2.... then i dont know how to install from tar.bz2..... but i know how to install from .deb and rpm(using alien) but i dont know how to installing from tar.bz2...please help me guys...thanks for advance:confused:

---

### Post by unixeducation on 2009-02-15
Just out of curiosity, do you need this specific version of Wine? In other words, will be the version in the repository not work for your needs?

If you do need to proceed with your version, here's the general idea:

```

bunzip2 [the filename]
tar -xvf [the unzipped tarball]
cd [the new wine directory]
./configure
make
sudo make install

```

---

### Post by icejack_outlaw on 2009-02-15
i just follow ur instruction but not understood all..... here is what im done>>

[PHP] cd wine-1.0.1/
>>>./configure 
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
>>> make
make: *** No targets specified and no makefile found.  Stop.
>>> sudo make install
[sudo] password for : 
make: *** No rule to make target `install'.  Stop.


* the symbol ">>>" is my directory  [/PHP]

can u show me more detail for installing?

anyway thanks

---

### Post by oldos2er on 2009-02-16
You need to install (at a minimum) build-essential. I don't know what other dependencies Wine has--I'm sure the docs have that info.

---

