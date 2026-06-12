---
title: "Applying NVIDIA Flicker fix in 09.04?"
date: 2009-05-31
forum: Hardware
---

### Post by UKRoman on 2009-05-31
Hi there,

I'm quite new to Linux so please bear with me if I'm asking a daft question.

I am using a Sony Vaio with an NVIDIA Geforce Go 7600GT graphics card. Under Ubuntu 08.10 I had a problem whereby the screen flickered every few seconds. After some investigation and help from other sources it transpired that this was being caused by the NVIDIA graphics driver dynamically adjusting the clock speed depending on the current load. To get round this I had to insert the following line:

options nvidia_new NVreg_Mobile=1 NVreg_RegisteryDWords="PerfLevelSrc=0x2222"

to the file:

/etc/modprobe.d/options

Apparently this had the effect of fixing the GPU clock speed, and it worked - no more flicker. 

However in Ubuntu 09.04 that file seems to have gone and the flicker is back again. Try as I may I haven't been able to track down where this fix might be applied.

Does anyone have any ideas?

Many thanks, UKRoman

---

### Post by Vadi on 2009-05-31
Have you tried creating the file and seeing if it was read?

(I'm not sure what happened to it either)

---

### Post by UKRoman on 2009-05-31
That was a good idea! I've just tried it though and it doesn't work. Oh well, I guess I'll have to go back to the last version of Ubuntu.

Thanks, UKRoman

---

