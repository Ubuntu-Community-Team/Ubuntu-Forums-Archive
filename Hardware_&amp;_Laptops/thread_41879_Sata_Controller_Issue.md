---
title: "Sata Controller Issue"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by TheCondor on 2005-06-15
Hello everybody  :) 

Yesterday I bought a sata controller and a sata seagate drive. The sata controller is said to be supported in linux, because its a silicon image 3114 one. 

I tried to compile a kernel myself with the option for the controller enabled, but I failed so many times ( the last time something was wrong with links to the initrd or something that I couldnt find out how to resolve ) 

Is there any other way than compiling a kernel for this option to work? Couldnt a module be loaded instead of having to compile the kernel? ( I dont mind compiling the kernel, but I spend a lot of time without a positive result - it was the first time I attempted it so  ](*,)  ) 

Any help would be appreciated

---

### Post by tonym on 2005-06-15
Try with the standard kernel and load module sata-sil.

Not sure if that is correct but worth a try.

---

### Post by TheCondor on 2005-06-15
Mmm it seems that it worked, now do I mount my drive normally as always? ( mkdir /blabla mount /blabla ?? )

---

