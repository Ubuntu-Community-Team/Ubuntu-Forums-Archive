---
title: "Dual core?"
date: 2012-04-07
forum: Hardware
---

### Post by cody1233 on 2012-04-07
I have a Dell Mini with 2 intel Atom processors.  When I look at System Monitor, they make an exact mirror of each other.  I tried to use the 64-bit version of ubuntu, but that musst go by the width of the individual processors.  What can I do to make my system use both processors?

---

### Post by ahallubuntu on 2012-04-07
Your Dell Mini has only ONE Atom Processor, but it is "dual core."  Both the 32 bit and 64 bit versions of Ubuntu will automatically use both cores as needed.  You don't need to worry about that.  Instead, try to understand what it is you are seeing in regards to information about the various cores in your Dell's processor.

Some Atom CPUs are 32 bit only so you can't use the 64 bit Ubuntu on them.  List the exact model of the Atom CPU you have in your Dell and we can tell you for sure.  The 32 bit version of Ubuntu will work on either 64 bit or 32 bit processors, so it is safe to use in all cases.  The only reason not to use it is that the 32 bit version of Ubuntu may not see all of your RAM if you have more than about 3.5GB of RAM.

---

### Post by cody1233 on 2012-04-07
Processor 0: Intel(R) Atom(TM) CPU Z520 @1.33 GHz
Processor 1: Intel(R) Atom(TM) CPU Z520 @1.33 GHz

Information from System Monitor

---

### Post by intel 4004 on 2012-04-07
> **cody1233 said:**
> Processor 0: Intel(R) Atom(TM) CPU Z520 @1.33 GHz
Processor 1: Intel(R) Atom(TM) CPU Z520 @1.33 GHz

Information from System Monitor

That CPU doesnt support 64bit.

---

### Post by cody1233 on 2012-04-07
thanks!

---

### Post by ahallubuntu on 2012-04-07
> **cody1233 said:**
> Processor 0: Intel(R) Atom(TM) CPU Z520 @1.33 GHz
Processor 1: Intel(R) Atom(TM) CPU Z520 @1.33 GHz

Information from System Monitor

Exactly: a dual core Atom.  I have one in my Acer netbook as well.  Ubuntu sees each core as one logical processor.

---

### Post by Yellow Pasque on 2012-04-08
Just for the record, an Atom Z520 is not a dual core. It is a single core with hyperthreading (two virtual cores).
[http://ark.intel.com/products/35466/Intel-Atom-Processor-Z520-%28512K-Cache-1_33-GHz-533-MHz-FSB%29](http://ark.intel.com/products/35466/Intel-Atom-Processor-Z520-%28512K-Cache-1_33-GHz-533-MHz-FSB%29)

---

