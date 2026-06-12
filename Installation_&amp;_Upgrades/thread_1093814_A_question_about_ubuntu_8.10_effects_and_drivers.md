---
title: "A question about ubuntu 8.10 effects and drivers"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Dustin2128 on 2009-03-11
is there any way whatsoever of keeping the "legacy" (what?) nVidia Geforce 4 driver working by installing only certain packages on upgrade from 8.04? A question though, working with open source software, why are the "legacy" (again, what the-) cards like the geforce 4 unsupported. Another question:I initially installed 8.10 with wubi, and it proved unstable, so I went and wiped it and installed 8.04 with a drive partition instead. Why is it that the driver seemed to work just fine with wubi under 8.10, yet when I try to upgrade, it says that there is no equivalent driver available, and I'd have to just go with out the effects. I can't go w/o the effects, it's out of the question. 
EDIT: also, I'm not able, nor willing to buy a new graphics card, as the one I have I know for a fact can handle anything I have thrown at it for the past few years with ease. Who really needs more than 128MB of video ram? well, maybe the gamer, but I've never encountered games I can't play with it.

---

### Post by martrn on 2009-03-12
> **Dustin2128 said:**
> Is there any way whatsoever of keeping the "legacy" (what?) nVidia Geforce 4 driver working by installing only certain packages on upgrade from 8.04?

Err no.  Kernel_modules or Driver are compiled (or binary blobbed+sewn together) based on the kernel and kernel headers.  Ubuntu is based on the Linux kernel and a new version of Ubuntu will have a newer linux kernel.  Keeping a kernel module for an older kernel will do you no good / won't work.

> **Dustin2128 said:**
> A question though, working with open source software, why are the "legacy" (again, what the-) cards like the geforce 4 unsupported.

[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html") has drivers that you can install (from a terminal mode) against any kernel (including one you compiled yourself) and against any distribution of linux.  They are supported by nvidia.  They are not supported by ubuntu and in the repositories becuase ubuntu is released with the latest software and the newer drivers compiled against stock ubuntu kernels.

> **Dustin2128 said:**
> Another question:I initially installed 8.10 with wubi, and it proved unstable, so I went and wiped it and installed 8.04 with a drive partition instead. Why is it that the driver seemed to work just fine with wubi under 8.10, yet when I try to upgrade, it says that there is no equivalent driver available, and I'd have to just go with out the effects. I can't go w/o the effects, it's out of the question.  EDIT: also, I'm not able, nor willing to buy a new graphics card, as the one I have I know for a fact can handle anything I have thrown at it for the past few years with ease. Who really needs more than 128MB of video ram? well, maybe the gamer, but I've never encountered games I can't play with it.

[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
Install the nvidia driver the non-recommended way.  (unsupported), and it should work.

Webi is supported but the whole file system becomes just one file on another system that is not very secure.  I (personally) wouldn't recommend installing webi, for lots of reasons, but see no problems with installing nvidia drivers manually.

---

