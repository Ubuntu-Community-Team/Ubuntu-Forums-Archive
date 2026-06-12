---
title: "Installing latest NVIDIA with recompiled kernel"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by nalmeth on 2006-04-06
I am following "HOWTO: Latest NVIDIA drivers" to get 3d accel going. The NV driver didn't seem to work for me, because it didn't give me any 3d accel.
I installed ubuntu on my friends computer (the one who gave me this nvidia card from that very computer), and 3daccel worked quite well.
I think it has come down to a problem with my kernel, though it won't say that anywhere. I have recompiled for preemption for Ubuntu Studio, and when doing the nvidia installing by hand, I can't install:
(METHOD 1)
linux-restricted-modules-`uname -r`
(METHOD 2)
linux-image-386 linux-headers-386
Because there are no packages found for my kernel:
```
nalmeth@edubuntu:~$ uname -r
2.6.12-50preempt
``` 
Is there a special name for this type of kernel? Or would the regular 386 work fine?

---

