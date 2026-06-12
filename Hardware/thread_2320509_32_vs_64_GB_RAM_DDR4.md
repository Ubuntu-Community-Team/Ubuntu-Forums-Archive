---
title: "32 vs 64 GB RAM DDR4"
date: 2016-04-14
forum: Hardware
---

### Post by ADRIAN_FLORIN_LAZA on 2016-04-14
Hello,

I want to build a system with Ubuntu for me.
I want to use it for 
- work on Android apps with Android Studio
- OpenCL
- Embedded C, Arduino, ..
- work on apps developed in Swift language
- use Matlab for machine learning algos
- develop Ubuntu apps
- and any other cool stuff

the mobo it seems will be - Gigabyte GA-Z170-HD3P
[http://www.gigabyte.com/products/product-page.aspx?pid=5495#ov](http://www.gigabyte.com/products/product-page.aspx?pid=5495#ov)

I chose as CPU an intel skylake i7 6700 - for Hyperthreading more specific ( 8 threads / 4 cores )
for OpenCL / other uses I wil use the integrated graphic intel HD 530 - after 2 years I will get something like ATI R9 nano

I have already a SSD Crucial MX100; + 1 HDD 7200 rpm
after 2 years I will get some SSD NVM on PCIExpress ( for speed up-to 5-6x comparing to SSD .. the pricess wil go down to current SSDs by then )

I will have 2 monitors - in one monitor I want to have on display always at hand manuals, books, videos with help and so on ..
On another one the code editor and so on.

I don't know how much ram to chose - 32 or 64 GB ?
I want to have this Ubuntu machine to depend on it, to work with it, at least 5-7 years.

I know that Linux / Ubuntu use RAM to protect SSD.. more RAM = the better

Does is efective to have 64 GB instead of 32 GB ? 
Would be a waste of money to throw in 64 GB of RAM ?

Thank you !

---

### Post by frostschutz on 2016-04-14
For most people, 32GB will already be more than plenty, even if you do use virtualization (which uses/wastes a lot of RAM simply for the sake of giving each VM enough air to breathe).

From your description alone it sounds like 16GB should already be plenty.

You can always upgrade RAM later if you actually see a need to do so.

> I know that Linux / Ubuntu use RAM to protect SSD

Not sure where you heard that but ... neither does it protect SSD nor do SSD need such protection... basically SSD is something you can just use and not worry about (aside from making backups of your important data, which you must do regardless what kind of storage medium you use).

---

### Post by ADRIAN_FLORIN_LAZA on 2016-04-15
I forgot ..
I would also use vmware / virtualbox to run OSX, it does some cool tricks and I'm used to it ( I'm using a macmini since 2009; Windows only at job, no Windows at home :) )
How fluid / speedy can run the virtualized OSX on this machine ( i7 with 8 threads, 32/64 GB, SSD ) ?
Does it is the virtualized OSX hardware accelerated ? can I access OpenCL or launch Xcode to creat iPhone apps with emulator inside guest OSX ?

---

### Post by QIII on 2016-04-15
While you may run any OS you choose on Apple hardware, it is a violation of Apple's EULA to install any of it's OSes on any hardware but Apple's.

We do not support violations of EULAs, ToS, etc.

Closed.

---

