---
title: "ltmodem"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by ottothecow on 2006-08-22
I have a thinkpad T23 that has run kubuntu fine for a long time (and mandrake before that) but I need to use its modem for the first time ever.

What I ahve discovered is that the Lucent PCI winmodem is supported by ltmodem.  there 2.6 ltmodem things can be found here: [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

There are even ubuntu packages but they dont install because they are looking for kernel-image-2.6.*.*. and linux-image-2.6.*.* which are not the versions I have.  Trying to install these with apt-get also fails.

Could someone please point me toward a packaged version that will work with a fully up to date dapper installation or else help me compile it for myself?

---

### Post by ottothecow on 2006-08-22
bump

---

### Post by mpvano on 2006-08-22
If you're NOT using Dapper, then the current Dapper packages obviously won't work!

I had my old Thinkpad 1400 working under breezy using the source package from the repositories for breezy. Building it was fairly complicated, but it worked fine.

The current version of Ubuntu distributes built ltmodem modules in the 386 kernel, but due to the fact that ubuntu no longer distributes a Dapper single processor 686 version, you can't use ltmodem unless you are using the basic 386 kernel (apparently the ltmodem sources are not easily modified for SMP). The SMP kernel is used by single processer Dapper installs and works fine except for the odd module like this that's out of date....

I think your choices are to upgrade and then just install the sl-modem utilities (and boot a 386 kernel when you need to use the modem), or to make sure you have all the breezy repositories enabled and install build-essentials, gcc-3.4, module-assistant, and the lucent modem sources and try to build that (assuming you're using breezy). If you're using something older than that, I think you've got a problem....

hope this gets you started...

Mario

---

