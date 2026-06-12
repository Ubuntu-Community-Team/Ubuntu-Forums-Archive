---
title: "How much RAM does Linux recognize?"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by jefuchs on 2008-02-13
I keep reading that Windows only utilizes 2.8 GB of RAM.  What about Linux?  

I currently have 2GB.  Would an upgrade to 4GB be a waste, or can it use it all?

---

### Post by Existentialist on 2008-02-13
Any 32-bit operating system will recognize between 2.5-3.25GB of RAM with 4GB installed.  If you use a 64-bit operating system you can utilize all 4GB.  So you will see a slight increase in RAM if you upgrade to 4GB and use the i386 Ubuntu, but with your amd supporting 64-bit there is no reason to not use the AMD64 version of Ubuntu which will also allow you to get the most of your upgrade to 4GB or RAM.

---

### Post by miesnerd on 2008-02-13
> **Existentialist said:**
> Any 32-bit operating system will recognize between 2.5-3.25GB of RAM with 4GB installed.  If you use a 64-bit operating system you can utilize all 4GB.  So you will see a slight increase in RAM if you upgrade to 4GB and use the i386 Ubuntu, but with your amd supporting 64-bit there is no reason to not use the AMD64 version of Ubuntu which will also allow you to get the most of your upgrade to 4GB or RAM.

Im currently running 64 bit ubuntu with 5 GB of ram (got 2x2GB for pretty cheap, not that I need 5 GB).

---

### Post by sgleo87 on 2008-02-13
I have 3 GB installed right now and all of it is recognized by the 32bit version of Ubuntu. So if you still want to run the 32bit version this is as high as you can go. For 4GB and up you can use the 64bit version like the others said above.

---

### Post by jefuchs on 2008-02-14
Thanks for the replies.  I considered the 64 bit Ubuntu but decided against it because I want to continue using VirtualBox, which says it does not work in 64 bit systems.

Anyway, if I get a chance to upgrade to 3 GB Ram in the future I just might do it.

---

### Post by regomodo on 2008-02-14
PAE is a method of implementing lots of RAM in a 32bit OS by mapping the limited address space (2^32) to the physical amount of RAM you have (max 2^36 usually). However, this depends if you're CPU can allow that.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Better of using a 64bit OS

---

### Post by schneiko on 2008-02-14
I'm running Ubuntu 7.10 with 4GB RAM. Ubuntu recognizes 3GB (3107856k total) of it.

In addition to that my onboard-gpu is using 256MB of shared memory, so I''m "losing" ~750MB of Ram. I wasn't aware of that fact when I bought the extra memory, but as it's pretty cheap right now, I don't really care...

Some day I'll upgrade to 64bit anyway, I guess.

---

### Post by jocko on 2008-02-14
> **jefuchs said:**
> Thanks for the replies.  I considered the 64 bit Ubuntu but decided against it because I want to continue using [COLOR=Red]VirtualBox, which says it does not work in 64 bit systems.[/COLOR]

Anyway, if I get a chance to upgrade to 3 GB Ram in the future I just might do it.

Virtualbox works **very well** on 64 bit systems (I know, I do it myself), but as far as I know it can not run a 64 bit **guest**.
So that's no reason for you to stay in 32bit.

---

