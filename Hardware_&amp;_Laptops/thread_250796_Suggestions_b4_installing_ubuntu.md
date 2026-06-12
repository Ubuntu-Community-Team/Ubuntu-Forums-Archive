---
title: "Suggestions b4 installing ubuntu"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by jsvidyad on 2006-09-04
Hi!!

  I got a laptop (dell E1505) with 2.16 GHz Core 2 Duo processor, 2 GB RAM , a NVidia GeForce Go 7300 card an Intel Pro/Wireless 3945 wireless adapter. I guess I am supposed to install an amd64-smp kernel. With this kernel, will ubuntu be automatically able to use both cores or is there anything else to be done to get ubuntu to utilize both cores??

  Also, i remember having read sometime ago about something that has to be done for linux to utilize all the system RAM if RAM > 1 GB. I did not have to worry about it earlier as my present PC has just 512 MB of RAM. Can someone tell me what I have to do to get support for 2 GB of RAM??

And any tips on how to use my video card and wireless adapter to work with 64 bit ubuntu would be really appreciated.

---

### Post by x64Jimbo on 2006-09-04
Your new machine sounds like a beast! Congrats!
The video card should work fine with the drivers from nVidia, the smp kernel will indeed allow you to utilize the processor's full potential, and it also includes himem support so you won't need to do anything special to see all 2GB of memory.

---

### Post by slibuntu on 2006-09-04
Ok i know this is irrelevant but **_WOW! WHAT A LAPTOP!_** I;m drooling all over my keyboard here! That is all!

---

### Post by jsvidyad on 2006-09-05
Can u tell me exactly which kernel I have to install fore a core 2 duo processor???

---

### Post by jsvidyad on 2006-09-05
Can u tell me exactly which kernel I have to install for a core 2 duo processor???

---

### Post by x64Jimbo on 2006-09-05
Does the core 2 duo use the EM64T instruction set? If so, that's Intel's codeword for "Yeah, we missed the boat on developing a 64 bit architecture, but there's no way we're using the letters A, M, and D in any of our product specs, so we'll just use the same amd64 instruction set but give it our own name."

---

### Post by jsvidyad on 2006-09-05
Yes, it uses EM46T

---

### Post by x64Jimbo on 2006-09-05
Then all you need is the amd64 kernel with smp.

---

