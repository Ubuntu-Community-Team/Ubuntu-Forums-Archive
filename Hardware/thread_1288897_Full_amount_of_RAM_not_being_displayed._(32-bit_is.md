---
title: "Full amount of RAM not being displayed. (32-bit issue?)"
date: 2009-10-11
forum: Hardware
---

### Post by Emancipation on 2009-10-11
[SIZE="2"]I've read some on this topic, but I'm rather uneducated on the whole curve between 64 bit and 32 bit. Anywho...
When I start up and head to the BIOS, it shows I have 4X 2048MB DDR2 RAM installed. However, when I boot up to gOS 3.1 (Ubuntu Hardy), it shows I only have 3.2 GB installed. I know this is rather unimportant, but I just want to know if all of this talk on RAM utilization on 32 bit systems is true. I feel as if my system is empty or not being used to its full potential.
*IF* this has to do with 32 bit systems, is there a way I can do over to 64-bit Ubuntu without reinstalling as a whole?

Thanks in advance,
~Nick[/SIZE]

---

### Post by Dark_Stang on 2009-10-11
32 bit supports a max of 3-3.5 GB of memory. Install 64 bit and it will support up to 128GB of memory. You will have to reinstall your OS, but all your files will stay as long as you don't reformat the partition /home is on.

---

### Post by Emancipation on 2009-10-12
[SIZE="2"]Thanks a bunch for clearing that up. :-)
~Nick[/SIZE]

---

### Post by scorp123 on 2009-10-12
> **Dark_Stang said:**
> 32 bit supports a max of 3-3.5 GB of memory. Aaah, the lost art of mathematics:

32-bit == **2^32 = 4294967296**

4294967296 Bytes ... if we divide that by (1024*1024*1024) we get = **_4 GB RAM_**

The reason you see between 3.2 GB and 3.5 GB of RAM is that the graphics memory and the BIOS have to fit in there as well or else they would not be addressable. Hence the "lost RAM": the available RAM is reduced so the system is able to map the graphics memory and the BIOS within that 4 GB limit somehow. Tadaaa.

There is a mechanism called "Physical Address Extension" that breaks the limit. The "Ubuntu Server" 32-bit kernel uses it per default (as do many distros as well, e.g. OpenSUSE, CentOS, Red Hat, Fedora ...). So if you install the "linux-server" package (if you do: make sure you also get all needed dependencies such as "linux-headers" and what not or else strange things might happen, especially to WiFi and Nvidia cards ...) you will be able to address up to 64 GB of RAM. Why? The "PAE" feature extends the addressable memory up to 36-bit

2^36 = 68719476736 ... = 64 GB

With a "PAE"-enabled 32-bit kernel the kernel itself will see up to 64 GB RAM. Individual processes are still limited to 32-bit = 4 GB of memory per process.

Usually this should be enough and work tip top. I had to use 32-bit+PAE for years on Linux because a commercial application that I have to use wasn't available yet for 64-bit Linux and I have never noticed any negative side effects.


> **Dark_Stang said:**
>  Install 64 bit and it will support up to 128GB of memory. My servers here all run 64-bit Linux and they have up to 512 GB of RAM. You may want to recalculate that maybe?

2^64 = ?

:D

---

