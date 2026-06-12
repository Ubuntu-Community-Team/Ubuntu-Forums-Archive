---
title: "64bit hardware question"
date: 2018-03-27
forum: Hardware
---

### Post by zoobuntufan on 2018-03-27
Hello friends, I'm a new Ubuntu user. I inherited an older PC with [this motherboard]("https://www.asus.com/Motherboards/P5QLEM/specifications/"). It currently has a Pentium processor & I see that I can upgrade it to an [Intel Core 2 Duo E6700]("https://ark.intel.com/products/27251/Intel-Core2-Duo-Processor-E6700-4M-Cache-2_66-GHz-1066-MHz-FSB") which is listed as 64bit.  My question is, is it only the processor that makes a system 32/64 bit? If I upgrade to the Core 2 Duo, will my currently 32bit system be upgraded to a 64bit?  I'm just looking to "future proof" this system for LTS updates in the coming 64bit only versions of Ubuntu.  Thanks for your time and your help!

---

### Post by Yellow Pasque on 2018-03-27
The motherboard chipset has to support 64-bit as well, but it should not be an issue for a G43 chipset. Your current CPU may support 64-bit as well, depending on which model Pentium it is.

---

### Post by zoobuntufan on 2018-03-27
Thanks for the information! Very helpful. The current processor I have is the [Pentium 4 3.00GHz]("https://ark.intel.com/products/27497/Intel-Pentium-4-Processor-supporting-HT-Technology-3_00-GHz-1M-Cache-800-MHz-FSB") which is 32bit.

---

### Post by zoobuntufan on 2018-03-27
Total newb question but the current CPU heatsink & fan that is on the Pentium CPU could be reused on an upgraded Core 2 Duo CPU?

---

### Post by Yellow Pasque on 2018-03-27
Yeah, you should be able to reuse the heatsink. Your current CPU runs significantly hotter than the CPU you're looking to buy (89W vs. 65W).

---

### Post by zoobuntufan on 2018-03-27
Perfect! Thanks again for your help. 8-)

---

### Post by mörgæs on 2018-03-27
> **zoobuntufan said:**
> I'm just looking to "future proof" this system for LTS updates in the coming 64bit only versions of Ubuntu.

18.04 LTS is available as 32 or 64 bit as usual giving you software to 2023 at least. What the next LTS will be I don't know but I haven't heard of any decisions to abandon 32 bit.

---

### Post by Yellow Pasque on 2018-03-27
> **mörgæs said:**
> 18.04 LTS is available as 32 or 64 bit as usual giving you software to 2023 at least. What the next LTS will be I don't know but I haven't heard of any decisions to abandon 32 bit.

Ubuntu stopped making official full desktop install iso's for 32-bit. You can still get minimal and net install 32-bit isos. Also, some flavors will continue making 32-bit install isos (like Xubuntu and maybe others).
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by mörgæs on 2018-03-28
Yes, the only change is that the installation process now begins with another ISO. It seems to mislead a lot of posters to think that 32 bit support is gone.

---

### Post by zoobuntufan on 2018-03-28
I was under the impression 32bit support was being discontinued as it was for Arch. Good to know it will still be available.

---

### Post by mörgæs on 2018-03-28
It certainly will. Please correct misunderstandings if you happen to find any.

If the problem is solved please mark the thread so (using Thread Tools).

---

### Post by deadflowr on 2018-03-28
fwiw, they have dropped 32-bit server editions going forward.
[https://lists.ubuntu.com/archives/ubuntu-release/2017-December/004257.html]("https://lists.ubuntu.com/archives/ubuntu-release/2017-December/004257.html")
though this would not affect mini.iso, I would assume.
(Or what any other flavor team decides to do)
Just an fyi

---

### Post by mörgæs on 2018-03-28
Yes, there might be less ISO's available but beginning from a mini.iso one can still install server software on 32 bit hardware.

---

