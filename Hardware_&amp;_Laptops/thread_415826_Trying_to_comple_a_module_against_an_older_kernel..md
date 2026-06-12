---
title: "Trying to comple a module against an older kernel..."
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by rchille on 2007-04-20
Hello Ladies and Gents,

I'm currently trying to get a Ralink driven minipci card to work under a stripped down variant  of Ubuntu called Pyramid. the catch is that they do not have 'make' or anything else to install or compile packages! 

Not a problem!  I followed a thread on the Pyramid's msg board and in theory I should be able to pull the kernel source for the verison that Pyramid uses, confuge it with Pyramid's .config file and then compile the rt2500 drives that I need against that kernel. 

The problem I'm having is I don't know how to compile the module against a kernel that is not installed and running [Pyramid is designed for embedded systems and complains loudly when I try to install it]. I poked around google but haven't been able to hit on the right search :( 

Thanks in advance!
Rob

---

### Post by rchille on 2007-04-23
Alright guys, I found the answer so for those of you who are having the same trouble::

What you want to do is specify the kernel modules that you want make to use.

in my case, I downloaded the kernel I wanted from [www.kernel.org]("http://www.kernel.org") and followed this wonderful [giude.]("http://ubuntuforums.org/showthread.php?t=56835"). 
I stopped short of actually compiling and installing the kernel, just ran the config [oldconfig] and made the link:
```
ln -s /usr/src/linux-old-kernel /usr/src/linux
```

Once I had my brand new [or in my case old] kernel I went to the directory that contained the make file for the module I wanted to compile. and ran the following:

```
make KERNDIR=/usr/src/linux
```

BECAREFUL! the KERNDIR id might not be standard for all make files. I did a "vi Makefile" and saw that was the identifier for the path to the kernel. Other makefiles might be different, I'm not good enough to be an authoritive source on that.

After the compile finished, I scp'ed the driver over and it worked!!!

Good luck on this if you are trying the same!

---

