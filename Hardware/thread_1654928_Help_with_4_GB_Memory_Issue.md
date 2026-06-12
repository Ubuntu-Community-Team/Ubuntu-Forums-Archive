---
title: "Help with 4 GB Memory Issue"
date: 2010-12-29
forum: Hardware
---

### Post by gdiloren on 2010-12-29
I bought and installed  4 GB (DDRR-2) RAM about 10 months ago. Under Vista, it listed correctly 4 GB in the Computer's properties then I installed Maverick (over?) Vista with Live Cd and I just checked my system monitor and it just tells me I use 500 MB ogf 3.3 GB Ram. So, I lost 0.7 GB!!! How can it be??? Is it Ubuntu or did the memory burned?:popcorn:

---

### Post by plucky on 2010-12-29
> **gdiloren said:**
> I bought and installed  4 GB (DDRR-2) RAM about 10 months ago. Under Vista, it listed correctly 4 GB in the Computer's properties then I installed Maverick (over?) Vista with Live Cd and I just checked my system monitor and it just tells me I use 500 MB ogf 3.3 GB Ram. So, I lost 0.7 GB!!! How can it be??? Is it Ubuntu or did the memory burned?:popcorn:

Open a terminal and post output of ```
uname -a
free -m
```

---

### Post by tech-hero on 2010-12-29
what ubuntu version did you install? did you install the 32-bit or the 64-bit?

---

### Post by cascade9 on 2010-12-29
You'll just need the PAE kernel. With PAE 32bit systems are limited to 3.something GB of RAM. 

IIRC ubuntu is meant to install the PAE kernel if it detects 4GB+ on install. No idea why it didnt work for you.

---

### Post by SnickerSnack on 2010-12-29
> **gdiloren said:**
> I bought and installed  4 GB (DDRR-2) RAM about 10 months ago. Under Vista, it listed correctly 4 GB in the Computer's properties then I installed Maverick (over?) Vista with Live Cd and I just checked my system monitor and it just tells me I use 500 MB ogf 3.3 GB Ram. So, I lost 0.7 GB!!! How can it be??? Is it Ubuntu or did the memory burned?:popcorn:

Afaik, you need a 64-bit OS to use more then ~3.3 gigs of ram.

Every bit of ram needs to have an address in order to be used, but addressing 4 gigs of ram requires addresses (that is, numbers) that are larger than a 32-bit system can handle.

---

### Post by cascade9 on 2010-12-29
> **SnickerSnack said:**
> Afaik, you need a 64-bit OS to use more then ~3.3 gigs of ram.

Every bit of ram needs to have an address in order to be used, but addressing 4 gigs of ram requires addresses (that is, numbers) that are larger than a 32-bit system can handle.

No, you dont need 64bit to see 3.3GB+. 

> **Physical Address Extension** (**PAE**) is a feature to allow [x86]("http://en.wikipedia.org/wiki/X86") processors to access a physical address space (including [random access memory]("http://en.wikipedia.org/wiki/Random_access_memory") and memory mapped devices) larger than 4 [gigabytes]("http://en.wikipedia.org/wiki/Gigabyte").[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

> [Physical Address Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension") is a technology which allows 32 bit operating systems to use up to 64 Gb of memory (RAM), something which is normally achieved by switching to a 64 bit system.[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by gdiloren on 2010-12-29
> **SnickerSnack said:**
> Afaik, you need a 64-bit OS to use more then ~3.3 gigs of ram.

Every bit of ram needs to have an address in order to be used, but addressing 4 gigs of ram requires addresses (that is, numbers) that are larger than a 32-bit system can handle. Here is :
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3266        947       2319          0         53        394
-/+ buffers/cache:        499       2767
Swap:        11998          0      11998
Linux 2.6.35-24-generic-pae #42-Ubuntu SMP Thu Dec 2 03:21:31 UTC 2010 i686 GNU/Linux
Fact is on 32 bit machine I was running 4 GB on Vista, now I happen to check on Maverick it gives me only about 3.3 GB, so I'm a bit puzzled!

---

### Post by gdiloren on 2010-12-29
I checked in my synaptic manager and my pae is installed. So I really read total ram as 3.3 GB. I still think it should be 4 GB unless something has gone broken!!! Also my Ubuntu version is 10.10.

---

### Post by gdiloren on 2010-12-29
I browsed some threads on this forum and nobody with 32 bits machine has a 4 GB RAM shown even with 4 GB sticks. So I guess it's like that!!

---

### Post by cascade9 on 2010-12-30
I've seen 4GB on 32bit with PAE. Well, 3.9GB, unlike windows linux doesnt tell little fibs about avaible memory (there is always some RAM reservered for system use, and any onboard devices like sound cards, network cards, etc will use some RAM as well).

---

### Post by Quadunit404 on 2010-12-30
I have 4GB RAM as well (stock DDR3 RAM that came with laptop) and both Windows and Ubuntu report 3.7GB is usable. Don't know why Ubuntu is reporting less RAM than Vista for you (I have Windows 7 HP 64-bit and Ubuntu 10.10 64-bit) but try creating a live USB of the 64-bit version of Ubuntu, then popping that into a free USB port and seeing if it correctly reports the amount of usable RAM.

Unless there are some services on your system that really require 0.7GB of your RAM, I believe, as suggested before, you're using the 32-bit version of Ubuntu and the PAE kernels are disabled for whatever reason.

---

### Post by gdiloren on 2010-12-31
> **Quadunit404 said:**
> I have 4GB RAM as well (stock DDR3 RAM that came with laptop) and both Windows and Ubuntu report 3.7GB is usable. Don't know why Ubuntu is reporting less RAM than Vista for you (I have Windows 7 HP 64-bit and Ubuntu 10.10 64-bit) but try creating a live USB of the 64-bit version of Ubuntu, then popping that into a free USB port and seeing if it correctly reports the amount of usable RAM.

Unless there are some services on your system that really require 0.7GB of your RAM, I believe, as suggested before, you're using the 32-bit version of Ubuntu and the PAE kernels are disabled for whatever reason.
Thanks and Happy New Linux Year to all !!! :KS
You have 64 bits. How would you re-able the PAE kernels on a 32 bits machine? My synaptic manager says they are installed!
Thanks!):P

---

### Post by gdiloren on 2010-12-31
> **Quadunit404 said:**
> I have 4GB RAM as well (stock DDR3 RAM that came with laptop) and both Windows and Ubuntu report 3.7GB is usable. Don't know why Ubuntu is reporting less RAM than Vista for you (I have Windows 7 HP 64-bit and Ubuntu 10.10 64-bit) but try creating a live USB of the 64-bit version of Ubuntu, then popping that into a free USB port and seeing if it correctly reports the amount of usable RAM.

Unless there are some services on your system that really require 0.7GB of your RAM, I believe, as suggested before, you're using the 32-bit version of Ubuntu and the PAE kernels are disabled for whatever reason.
I tried booting into the 64 bits edition successfully but the RAMs shown are identical to what's shown in the 32 bit edition, i.e. 3.2 GB in system monitor. I guess I'm right, I've burned some modules in my stick in the motherboard!

---

### Post by cascade9 on 2011-01-01
> **gdiloren said:**
> I tried booting into the 64 bits edition successfully but the RAMs shown are identical to what's shown in the 32 bit edition, i.e. 3.2 GB in system monitor. I guess I'm right, I've burned some modules in my stick in the motherboard!

I'd doubt it. More likely you are using system RAM for onboard chips (video card, network, sound card, etc)

---

### Post by gdiloren on 2011-01-02
> **cascade9 said:**
> I'd doubt it. More likely you are using system RAM for onboard chips (video card, network, sound card, etc)
Thanks! And Happy New Year,  too!!!:guitar:

---

### Post by cascade9 on 2011-01-02
No problem, happy new year for you as well ;)

---

