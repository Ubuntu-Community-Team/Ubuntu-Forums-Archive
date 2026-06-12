---
title: "I am trying to compile a 16.04 kernal with no luck."
date: 2016-09-20
forum: Hardware
---

### Post by Robert_Jackson on 2016-09-20
I have a MacBook pro that has the hang on shutdown and the gets really hot problem when closing the lid.
This problem has a documented patch that requires downloading the source for the kernel and pasting 4 lines into a source file.
All that went fine.
When I tried to compile it didn't work.
So off I went to the BuildYourOwnKernel wiki at [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

I get to step three and I am dead in the water.
This command to download the build kernel packages fails.

```
sudo apt-get build-dep linux-image-$(uname -r)
```

Help!

---

### Post by T.J. on 2016-09-20
> **Robert_Jackson said:**
> I have a MacBook pro that has the hang on shutdown and the gets really hot problem when closing the lid.
This problem has a documented patch that requires downloading the source for the kernel and pasting 4 lines into a source file.
All that went fine.
When I tried to compile it didn't work.
So off I went to the BuildYourOwnKernel wiki at [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

I get to step three and I am dead in the water.
This command to download the build kernel packages fails.

```
sudo apt-get build-dep linux-image-$(uname -r)
```

Help!

There are many things that can cause a compiler to abort. In order to help you at all, I need:

1. The error message from the compiler or other tool. 
2. The kernel version number you are trying to compile. (In order to test.)
3. The source of the kernel patch you are trying to apply. (for testing)
4. The version number of Ubuntu you are currently using. (In order to use the same tools.)
5. The processor type you have. (In order to set the compiler)
6. The version number of GCC. (In order to verify setup) 

I'm sorry, but all of that is actually necessary in order to offer you any kind of real help solving this.

You can get the GCC version number using 

> gcc -v

---

