---
title: "Mixing Dapper &amp; Edgy to get 2.6.17 kernel"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by l:x on 2006-07-31
Hello,

I'm running a nice Xubuntu 6.06 setup on my Dell Inspiron 9400. Everything works well, except for the SD/MMC-reader. I figured out that this one should work when installing the 2.6.17-kernel.

Because this kernel isn't in the Dapper-repos I changed my sourcelist to get the Edgy-repos. If I should install the 2.6.17-kernel from Edgy I need to install these ones:
```
linux-686-smp
linux-headers-686
linux-headers-2.6.17-5
linux-headers-2.6.17-5-686
linux-kernel-headers
linux-restricted-modules-686
linux-restricted-modules-common
linux-restricted-modules-2.6.17-5-686
linux-image-686
linux-image-2.6.17-5-686
linux-source
linux-source-2.6.17
module-init-tools
libc6-i686
libc6
libc6-dev
```

It doesn't seem to have a big impact on the rest of the packages. Could I safely install these from Edgy and get back to the Dapper-repos after that to maintain my other packages? Or isn't this a wise decision and could I better wait until 2.6.17 is released as stable in the Ubuntu-repos?

Greetings,
Niels R.

---

### Post by zhangzhuo_1999 on 2006-07-31
Very Good:KS

---

### Post by andb on 2006-07-31
Have you thought about just compiling a kernel from source? It'll work perfectly for you, yuo can take out some of the overhead that you dont need for your system, and itll be fun! There are lots of great howtos here how to do it.

---

### Post by adamkane on 2006-07-31
Ah-crazy-choo!

---

### Post by geos2 on 2006-07-31
when i did that, ssh locks up after a minute or so and lots of things stopped working...

---

### Post by evil_elman on 2006-07-31
I've tried to enable the Edgy-repos and do the same as the '**l:X**' above. It installs the packages OK and the kernel and OS is running fine on my laptop.

However, whenever trying to install packages, or do anything which involves compiling (or similar) I get errors about the 'locale' being incorrect or something like that.

I was also trying to install VMWare Server (which needs compiling). I've done it before with original kernel but with the Edgy kernel I'm not allowed to install 'build-essentials' from the repos which means I can't compile anything...

It's buggy... Be prepared...

Building it from source is something I don't know anything about, though...

---

### Post by andb on 2006-07-31
Try this kernel compile howto for example: [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel)

To be honest, you are safer doing the kernel compile. Youll still have the old one, and can boot to it in GRUB even if you totaly hose something. By mixing other packages, you can REALLY screw you system, and worse yet, you may forget what you did! (which is important if you want to REVERSE what you did!) Give it a try, nothign to lose ;)

---

### Post by l:x on 2006-08-01
Ok, I'll compile the kernel myself than. I've done it before, but I always spend too much time with it (in my opinion), so I thought there could be another easier (= quicker) way.
I rather like to spend some hours compiling the kernel instead of having a buggy system.

Thank you all for the response!!!

---

