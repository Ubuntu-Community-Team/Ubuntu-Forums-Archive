---
title: "nVidia 185.18.14 driver and kernel 2.6.30.2"
date: 2009-07-20
forum: Hardware
---

### Post by grayn0de on 2009-07-20
Does anyone know if the newest nVidia driver (185.18.14) works with the 2.6.30.2 kernel? I am a little wary about testing this on my system.

---

### Post by kpkeerthi on 2009-07-20
185.18.14 works with Kernel 2.6.30.**1**. Can't think of a reason why it should'nt work with **.2** minor patch release. Anyway, I have just downloaded the source (2.6.30.2). Will built it soon and post back how it went.

---

### Post by kpkeerthi on 2009-07-20
Works just fine. No problems with my 7800GTX.

---

### Post by grayn0de on 2009-07-21
Awesome. Thank you. 

I'll try this this weekend, perhaps. Last time I did, I used kernelcheck to grab and configure the kernel, but I forgot to purge the old nvidia dirvers. I just last night got that all straighted out. 

LOL. Lesson learned!

---

### Post by master_kernel on 2009-07-22
> **grayn0de said:**
> Awesome. Thank you. 

I'll try this this weekend, perhaps. Last time I did, I used kernelcheck to grab and configure the kernel, but I forgot to purge the old nvidia dirvers. I just last night got that all straighted out. 

LOL. Lesson learned!
Were you using Lumen? It should've automatically purged all nVidia packages. If not then I have some serious problems to deal with.

---

