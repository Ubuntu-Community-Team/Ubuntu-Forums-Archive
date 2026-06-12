---
title: "Patch Kernel"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by frogotronic on 2007-02-17
Hi,

I'm using 2.6.15-28-686 kernel and the 8776 nvidia drivers.  I am going to compile my kernel and patch it using the Suspend2 patch to enable hibernate.

I will use this guide:  [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)


BUT, how do I apply the suspend patch?

I've never done this before

- CH   :confused:

---

### Post by frogotronic on 2007-02-18
hmm...would I patch at the same time I "patch" with the nVIDIA source drivers?

---------------------------

10 minutes later...NOPE,

[I] think I should download the latest suspend2 can be downloaded from here:

[http://www.suspend2.net/downloads/all/suspend2-2.2-rc16-for-2.6.15.tar.bz2](http://www.suspend2.net/downloads/all/suspend2-2.2-rc16-for-2.6.15.tar.bz2)

extract to the /usr/src/linux-2.6.15 folder and ./apply to apply the patches [/I]

Would this be correct?

-CH

---

