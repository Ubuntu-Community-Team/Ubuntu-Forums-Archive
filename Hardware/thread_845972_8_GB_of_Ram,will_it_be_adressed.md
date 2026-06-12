---
title: "8 GB of Ram,will it be adressed?"
date: 2008-07-01
forum: Hardware
---

### Post by guitronics on 2008-07-01
I have two Motherboards with 8 Gigabytes of RAM. Will Ubuntu utilize all of the RAM? If not, how much RAM will Ubuntu utilize? Thanks.

---

### Post by thideras on 2008-07-01
You will need the 64bit version of Ubuntu to address more than 4gb of space.

---

### Post by Master Chief on 2008-07-01
> **guitronics said:**
> I have two Motherboards with 8 Gigabytes of RAM. Will Ubuntu utilize all of the RAM? If not, how much RAM will Ubuntu utilize? Thanks.

You should have mentioned the brand/type/specs of your motherboards, because that along with the BIOS is an important factor.

Anyway; Ubuntu 32bit will support 4GB and I am running amd64bit (Intel Q9300) with 8GB of RAM (I could use a lot more for a RAM drive).

---

### Post by zgornel on 2008-07-01
Actually, 32 bit 2.6 kernels support up to 64GB of memory with PAE (Physical Address Extension) support enabled. You have to either recompile kernel or use the server version of the kernel (not very sure about the latter).The standard generic kernel will see ~3GB of ram.
Further references: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by sdennie on 2008-07-01
As has been said, you'll have to run 64bit or use a 32bit PAE kernel.  The Ubuntu -server kernel has PAE enabled:

```

$ grep HIGHMEM64G /boot/config-2.6.24-19-server 
CONFIG_HIGHMEM64G=y

```

However, I don't think you can use the nvidia restricted drivers with that kernel (at the very least, I wasn't able manually install them because the server kernel identifies as a Xen kernel).  If for some reason you need to run 32bit with PAE and nvidia, you'll have to compile your own kernel.  

If possible, it's probably easiest to go 64bit.

---

### Post by guitronics on 2008-07-04
Thanks for the replies so far: I have an Asus Maximus Formula(Air cooled) and an Abit IP35Pro. I only have 1 decent CPU,a Core 2 Duo E6850.

I have 8GB (2 GB Modules) of Gskill low-latency DDR-2 for each mobo.

If I can run the 64-bit Version of Ubuntu, (NOT the server version),I'll be ecstatic.

I wouldn't even try to "Recompile the kernel"....OUCH!

---

### Post by zgornel on 2008-07-04
> **guitronics said:**
> Thanks for the replies so far: I have an Asus Maximus Formula(Air cooled) and an Abit IP35Pro. I only have 1 decent CPU,a Core 2 Duo E6850.

I have 8GB (2 GB Modules) of Gskill low-latency DDR-2 for each mobo.

If I can run the 64-bit Version of Ubuntu, (NOT the server version),I'll be ecstatic.

I wouldn't even try to "Recompile the kernel"....OUCH!

There should be no problems in running the 64bit version of Ubuntu :) on your system.

---

### Post by guitronics on 2008-07-04
I thank you all...from the Wiki, it looks as though if I use 64-bit linux,starting w/version 2.6 that "PAE" will make it accept the 8 GB. Ram.

Of course, this assumes the hardware (CPU) is compatible (64 bit).

                              Thanks again.

---

### Post by sdennie on 2008-07-04
PAE and 64bit are mutually exclusive.  One is a solution to extend kernel addressing space to 36bits and the other just runs the whole OS as 64bits.  If you have a motherboard that supports 8G of RAM, there is a very good chance that your machine will support both of these options but, it will probably be easiest for you to just install a 64bit version of Ubuntu.

---

### Post by guitronics on 2008-07-07
Thanks,Vor...64 bit it will be.:)

---

