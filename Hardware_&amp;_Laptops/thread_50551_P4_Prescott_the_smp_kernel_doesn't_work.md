---
title: "P4 Prescott: the smp kernel doesn't work"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by scorpio2002 on 2005-07-20
Hi there! I own a P4Prescott and I've just installed Ubuntu. I noticed that it didn't install automatically an smp kernel, so I went into Synaptic and i got one but it doesn't work properly. When I boot the smp kernel, after less than one minute, the screen simply freezes and the machine stops working hoplessly. The kernel I got was 2.6.10-7.

Well, I must admit that this used to happen when I had Fedora core 3, so I'd kinda got used to working with no smp. But some time ago when I installed Fedora 4 I realized that everything worked fine with the smp kernel. The kernel version was 2.6.12-1.

Now I think those freezes I get are due to the old smp kernel(v 2.6.10-7) which is available on apt. Do you know where I can get a newer version? Otherwise, you could help me find why that kernel freezes...

Just for you to know, these are my hw specs:

Asus P4P800-X, chipset Intel 865PE
P4 - Prescott 3000
RAM 512 Mb
Ati Radeon 7000
HD 80Gb IDE (Master)
HD 15Gb IDE (Slave)
DVD Sumsung TS-H552 (Master)
NEC CD Burner (Slave)
Audio and LAN on Board
Firewire card


Hope you can help me. :D Thank you ^^
Donato
Italy

---

### Post by spacemonkey on 2005-07-21
You could compile your own.  It's pretty easy to do.  This howto worked great for me.

[http://ubuntuforums.org/showthread.php?t=43065](http://ubuntuforums.org/showthread.php?t=43065)

---

### Post by scorpio2002 on 2005-07-21
Thank you spacemonkey. As I'm not very familiar with kernel configuration, I'd like to take the ubuntu kernel sources from apt and then apply the patch available on [www.kernel.org](www.kernel.org). This way, the configuration will remain the same and I would have only to add smp support :-)

My question is: how do I install a kernel patch to the sources?

---

### Post by spacemonkey on 2005-07-21
One way to keep your old configuration when compiling your own kernel is do use 'make oldconfig' instead of the regular config options.  If I understand it correctly, it will copy your current kernel config to the new kernel, and if there are any new options because it's a newer kernel version, it will ask you about those.

---

