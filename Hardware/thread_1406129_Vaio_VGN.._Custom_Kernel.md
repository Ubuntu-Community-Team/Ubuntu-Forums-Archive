---
title: "Vaio VGN.. Custom Kernel?"
date: 2010-02-13
forum: Hardware
---

### Post by HarshReality on 2010-02-13
I am just wondering as I have a Vaio VGN-NS325J. While the 'stock' kernel for Karmic is quite nice, has anybody tried or made a custom kernel for the thing to make it a bit more efficient (trimming the fat)? If so care to post details/tutorial or the like?

---

### Post by falconindy on 2010-02-13
There's no shortage of information on how to do this.

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)
[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)
[http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html](http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html)
[http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html)

I could go on... I recommend the first link, as it includes all of Ubuntu's patches, but does take a fair bit longer to checkout/configure/build than a vanilla approach.

Good luck.

---

### Post by HarshReality on 2010-02-13
Thanks for that.. hopefully an additional contribution will kick in that would give me specifics for the VGN

---

### Post by falconindy on 2010-02-13
I think you should familiarize yourself with the process before you start making any serious changes. The kernel config is enormous, and there's plenty of options that you can change that will prevent the kernel from booting, or even compiling.

That aside... If you want to strip out the unnecessaries, I suggest you take a look at the output of `lspci -vv` and `lsmod`. This will give you an idea of what modules you need to include. However, this will only reduce your compile time. If you want to increase performance (as slight as it will be), you need to look up your specific processor and change the appropriate options under the processor setup.

The real performance gains come from patches such as Con Kolivas's patchset.

I would advise you to take small steps...

---

