---
title: "update from single core to multi core CPU"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Torte74 on 2009-02-26
Hi,

I would like to get information about the correct way in updating my system, currently running Ubuntu 8.10 server i386 including the latest patch set. I would like to replace the CPU from Intel Celeron 1600 MHZ (Intel S420, 1 core) with an Intel Core 2 Duo E7400 (2 core).

What I did until now ...
The machine was installed with Ubuntu 8.10 i386 server with installed single core CPU. I installed Samba to use the server as a fileserver. Also the 3Ware tool 3dm2 is installed for the installed 3Ware 9650SE SATA Raid Controller. The server acts also as a VMWare Host => VMWare Server 2... and this, I think, would make the most trouble by changing from singlecore to multicore CPU by replacing/changing the kernel (SMP).

Can someone give me some hinds or documentation what changes needs to be done to change my Ubuntu system to use multi core CPU and also what steps needs to be done to have VMWare also working after changing kernel to SMP ...

regards Torsten

---

### Post by ddrichardson on 2009-02-27
If its just a kernel recompilation, then Arch has a good guide [here]("http://wiki.archlinux.org/index.php/Kernel_Compilation_From_Source"), except the current kernel config is:
```
cat /boot/config-`uname -r` > .config
```When you do your menuconfig then change the processor type. Our guide is [here]("https://help.ubuntu.com/community/Kernel/Compile").

---

