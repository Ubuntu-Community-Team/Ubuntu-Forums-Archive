---
title: "Why is my Atheros a restricted driver?"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by ajack on 2007-05-08
Hi all,

Just curious about this.  I upgraded to 7.04 (installed from 6.06 -> 6.10) and am wondering why Atheros is a restricted driver?  I thought the madwifi.org group was doing the drivers for linux?  Just curious.  Hope somebody can explain to me.  Not an emergency or anything like that, just curious.

-ajack

---

### Post by rufius on 2007-05-08
What driver is listed as being used with it I wonder?

A possibility I've thought of is maybe if madwifi is still considered beta?

---

### Post by tyler22 on 2007-05-08
Does it use closed source software?

Therefore makes it restricted? Thats my line of thinking.

---

### Post by ajack on 2007-05-09
> **tyler22 said:**
> Does it use closed source software?

Therefore makes it restricted? Thats my line of thinking.

Exactly, I thought the driver was taken from madwifi.org website... and should be completely open source... strange...

---

### Post by el toro on 2007-05-09
From a LWN article [here]("http://lwn.net/Articles/230967/"):

> MadWifi (which is an abbreviation for Multiband Atheros Driver for Wireless Fidelity according to the project's website) is a widely used driver for wireless cards, but it is not part of the Linux kernel and is unlikely to ever be. The driver relies on a 'Hardware Abstraction Layer' (HAL) that is only provided in binary form. The belief is that because the Atheros chips can be instructed to do various things that regulatory agencies (the FCC in the US for example) oppose, the code for doing that must be closed source. Rather than make the whole driver closed source, separating it into two pieces was done specifically to avoid the closed source portion being considered a derivative work of the kernel.

Because of the non-firmware binary blob, the driver will not be included in some 'free' distributions and users will need to find it from other non-official or less supported repositories. This could lead some users to not update their driver because the package management system did not alert them to the change. At some level, any publicity that makes more people aware of the problem is probably a good thing. 

---

### Post by ajack on 2007-05-11
@el toro:

Thanks, you have fed my curiosity.... :-)

That being said, why didn't Ubuntu use the OpenHAL for Atheros? URL [http://lwn.net/Articles/209472/](http://lwn.net/Articles/209472/)

Anyway, I am happy with my Atheros and hope a truly open source code gets adopted.

---

### Post by tyler22 on 2007-05-11
Yah it sucks having to use the closed source drivers, but I didnt buy my computers to get half the functions out of them.

---

### Post by dyrer on 2007-05-12
Get atheros Linux drivers at [http://www.atheros.cz/](http://www.atheros.cz/)

---

### Post by beorn! on 2007-05-13
@el toro

so what you are saying is that I can open synaptic, go into settings> reciprocities, make sure that multiverse and restricted software is downloadable from the internet, reload the package tree and update?    

oh man, that means i have to lug my computer into the living room... :(

---

### Post by stchman on 2007-05-14
> **ajack said:**
> Hi all,

Just curious about this.  I upgraded to 7.04 (installed from 6.06 -> 6.10) and am wondering why Atheros is a restricted driver?  I thought the madwifi.org group was doing the drivers for linux?  Just curious.  Hope somebody can explain to me.  Not an emergency or anything like that, just curious.

-ajack

In 6.10 the kernel for madwifi is restricted as well.  Restricted or not "work" is the key.

---

