---
title: "Kernel customization"
date: 2008-07-29
forum: Hardware
---

### Post by simion314 on 2008-07-29
Hi, i want to customize a kernel for my laptop, reason is to improve my boot speed by building the requiered modules into kernel.

First please do not reply to not do this, i want to do it, and i want to learn more about it.

What i have done.
1 i used lsmod to find the modules i need.
2 i edited the kernel .config (i made a small c# program) to build the modules into the kernel(there is a script on the web but i do not know bash and it didn't work for me). I do not found all the modules in lsmod in the .config
3 compiled the kernel in the debian way using kpkg
4 i had to crate a initrd image to boot the kernel because i had a kernel panic
resoults:
1 the kernel works, it boots in kde.
2. i am missing sound and the network card light is turned off
3 lsmod lists 20 lines now(the modules i do not found in .config.
4 the boot speed is the same

I need hel to:
1 debug the sound and network problem
2 build all my modules(requierd at start) into the kernel
3 stop udev autodetection at boot(modprobe take long time to load modules too
4 if someone is intrested maybe to improve my program of editing the kernel .config to be used by others.

P.S i am the guy that to learn so give me links to documentation

---

### Post by phidia on 2008-07-29
I think the Ubuntu [System Administration page]("https://help.ubuntu.com/community/SystemAdministration") would be very helpful for you.
And specifically the [Kernel HOWTO]("https://help.ubuntu.com/community/Kernel?action=show&redirect=KernelHowto") & [Boot Services]("https://help.ubuntu.com/community/BootServices") guides.

---

### Post by master_kernel on 2008-07-29
Try enabling Intel HD Sound under ALSA. Also, what is the lspci of your Ethernet card?

---

### Post by simion314 on 2008-07-29
Thx for response.the lspci of my ethernet is 04:00.0 Ethernet controller: ADMtek 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)  , when i custom compuled my kernel ,i compiled   many times the kernel and even i do not remove any modules i had the same problems. maybe i should use modprobe and try to load the module for my card, but i do not know what it could be, maybe e100

---

