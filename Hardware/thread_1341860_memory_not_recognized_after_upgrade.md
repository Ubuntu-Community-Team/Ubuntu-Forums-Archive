---
title: "memory not recognized after upgrade?"
date: 2009-11-30
forum: Hardware
---

### Post by kawazu on 2009-11-30
Folks;

ran into a peculiar behaviour just a few moments ago: Upgraded my Toshiba Tecra A8 notebook to 4 GB RAM (2 modules, 2 GB each). Booted into BIOS setup, saw 4096M RAM available. Fine. Booted into 9.10, ran a free -m:

```

[kr@n428 12:25:21] ~> free -m
             total       used       free     shared    buffers     cached
Mem:          3268        445       2823          0         75        206
-/+ buffers/cache:        163       3105
Swap:            0          0          0

```

Huh? Just 3 gigs total? Strange. Never seen anything like this before (unless living somewhere next to boundaries like > 4gig on a 32bit system). Running an up-to-date karmic installation... Any ideas where to look to track this down?

TIA and all the best,
Kristian

---

### Post by 3rdalbum on 2009-11-30
> **kawazu said:**
> Folks;

ran into a peculiar behaviour just a few moments ago: Upgraded my Toshiba Tecra A8 notebook to 4 GB RAM (2 modules, 2 GB each). Booted into BIOS setup, saw 4096M RAM available. Fine. Booted into 9.10, ran a free -m:

```

[kr@n428 12:25:21] ~> free -m
             total       used       free     shared    buffers     cached
Mem:          3268        445       2823          0         75        206
-/+ buffers/cache:        163       3105
Swap:            0          0          0

```

Huh? Just 3 gigs total? Strange. Never seen anything like this before (unless living somewhere next to boundaries like > 4gig on a 32bit system).

3.2 GiB is perfectly normal on a 32-bit operating system. It's a limitation of 32-bit operating systems - they can address 4 GiB total, INCLUDING video memory and I/O cache which takes up some of your address space. Which generally leaves people with 3.2 GiB usable.

If you have a Core 2-based model then you have a 64-bit processor, and you can use the 64-bit edition of Ubuntu. If you have the original Core-based or the Celeron-based unit, then you can try installing the PAE kernel (which may cause problems with proprietary drivers that have not been written for PAE) or just settle for 3.2 GiB of available RAM, which is still pretty big for Ubuntu.

---

### Post by JBAlaska on 2009-11-30
According to Mr. Google your lappy has a x86_64 processor, the best soloution would be to install 64bit Ubuntu as 3rdalbum mentioned. or you could install the PAE enabled kernel like so:
```
sudo apt-get install linux-generic-pae
```

---

### Post by 3rdalbum on 2009-11-30
> **JBAlaska said:**
> According to Mr. Google your lappy has a x86_64 processor, the best soloution would be to install 64bit Ubuntu as 3rdalbum mentioned. or you could install the PAE enabled kernel like so:
```
sudo apt-get install linux-generic-pae
```

I got a few results saying that they came with Core Duos, and some results that said Core 2 Duo. The latter is 64-bit, the former isn't. I assumed that there were earlier models and later models.

---

### Post by kawazu on 2009-11-30
> **3rdalbum said:**
> 3.2 GiB is perfectly normal on a 32-bit operating system. It's a limitation of 32-bit operating systems - they can address 4 GiB total, INCLUDING video memory and I/O cache which takes up some of your address space. Which generally leaves people with 3.2 GiB usable.


Hmmm, thanks for sorting me out here. So far I thought the 32-bit limit only applied to main memory, leaving especially video memory subject to management by the display controller. Oh well, you never stop learning... ;)

Installing the -pae kernel (quick shot) didn't really change much, so I'm off to having an x86_64 installation done and see what happens then. Thanks a bunch for your help, so far. :)

By the way yes the amount of memory is pretty well-scaled for an Ubuntu system, but it's all relative I guess: Given this is my everyday working notebook usually running a Java IDE (Eclipse or NetBeans), some application server (at the very least tomcat) and a backend RDBMS (SAP MaxDB, Oracle XE, ...), this size ain't that much altogether anymore. ;)

Cheers,
Kristian

---

### Post by kawazu on 2009-11-30
By the way;

> **kawazu said:**
> Folks;
```

[kr@n428 12:25:21] ~> free -m
             total       used       free     shared    buffers     cached
Mem:          3268        445       2823          0         75        206
-/+ buffers/cache:        163       3105
Swap:            0          0          0

```


Just running / installing 9.10 x86_64 and free -m does provide just the same output as above running on 32bit?

K.

---

