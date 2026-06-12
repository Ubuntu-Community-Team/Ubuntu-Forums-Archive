---
title: "gentoo performance"
date: 2008-03-18
forum: Gentoo and derivatives
---

### Post by hellfeuer on 2008-03-18
Two questions:

First, will gentoo performance be significantly better than some other distro with the same apps installed (i have a Core2 1.66 ghz and 1gb ram)? Better in terms of everyday usage: apps starting faster/more responsive etc

And on a related note, in any distro, what kind of performance increase can I expect by compiling the kernel myself?

thanks

---

### Post by erginemr on 2008-03-19
For a detailed one-to-one comparison:
[http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Gentoo](http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Gentoo)

I also believe that Gentoo, on which all packages are compiled, performs better than Ubuntu and pretty much most other distros, but this speed comes at a price. You need to be fairly competent in Linux, get your hands dirty and mess with config files a lot, so it is not for the faint of heart. The prize is big however; if you can survive this endurance test, you will find yourself transformed to a Linux geek. 

On the other hand, Ubuntu is much more newbie-friendly, as there is (almost) always an easy way to accomplish things. At the cost of having a slower system, I find Ubuntu better overall: from the viewpoint of a consistent look and set of tools, user-friendliness, 6-month release cycles and technical/monetary support by Canonical. 

And last by not least, the incredible Ubuntu users community here is a big plus, though Gentoo community -while less in number- is also renown to be very user friendly.

So, unless you are somewhat experienced in Linux, I suggest you to stay away from Gentoo and cut your teeth on Ubuntu for some time. You can use VirtualBox to simulate a Gentoo install to see if it works for you.

---

### Post by hellfeuer on 2008-03-19
Nono, I'm familiar with linux and have been using ubuntu for quite a while. I know gentoo has user friendliness problems, I was just curious whether the performance really is that much better

---

### Post by spupy on 2008-03-22
I don't use Ubuntu anymore, so I might not be very correct. Yesterday i installed Ubuntu 8.04 beta. My Gentoo install is running circles around it. But that may be gnome's fault, since i use fluxbox on Gentoo, and that Ubuntu is beta. The better performance on Gentoo comes from the fact the it runs only what you need, no unnecessary stuff. But to know what you need, you have to know your computer well, your software also.

But compiling your own kernel does make a huge difference on every distro. The Ubuntu kernel that everyone uses is loaded with all possible drivers, so that it will work for almost anyone. That is also true for the default Gentoo LiveCD kernel. After i compiled a kernel with only the stuff i need, it removed 10+ seconds from the boot time, and the kernel itself loads 2-3 times faster.

And Gentoo is not that hard if you know yourself with the CLI, follow the guidebook carefully and have patience.

---

### Post by hellfeuer on 2008-03-22
Thanks, that helped. I'll definitely compile a kernel on Ubuntu, and I think I'm going to end up trying out Gentoo as well soon. I'll post my results here when I'm done.

Any suggestions for benchmarks?

---

### Post by spupy on 2008-03-22
> **hellfeuer said:**
> Any suggestions for benchmarks?

Check the program "bootchart". With it you can measure your boot time. It also shows other interesting things about the boot process.

---

