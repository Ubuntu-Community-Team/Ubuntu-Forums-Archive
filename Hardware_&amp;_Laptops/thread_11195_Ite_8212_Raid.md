---
title: "Ite 8212 Raid"
date: 2005-01-14
forum: Hardware &amp; Laptops
---

### Post by cdean on 2005-01-14
I have one of these PCI RAID cards.  Nice buy - got it on eBay for $25.  It was elusive on Gentoo: I couldn't get it installed.  It seems, though, that I have it working on Ubuntu.

My method was to merge the steps in:
[Ubuntu KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto)
[ITE kernel compile](http://www.passys.nl/tips/ite_kernel_image_compile.txt)
[KernelNewbies FAQ](http://www.kernelnewbies.org/faq/)

Follow the wiki instructions through the Source section.  At that point, go get the -ac series patch from kernel.org for your kernel version, unless you are using 2.6.11 (which at the time of this writing, was still in rc1 stage).   2.6.11 is supposed to have the iteraid driver built-in/modulized.  Apply the patch using the instructions in the KernelNewbies FAQ.  Then follow the instructions in the ITE kernel compile document in the 2.6 -> in the kernel section.  Once you have that done, go back to the Ubuntu wiki page and finish out.

I'm still waiting for the kernel compile to finish because I've got a bad stick of RAM and it keeps segfaulting.  I'll update this as I progress.

---

### Post by cdean on 2005-01-15
Stupid Kingston ValueRAM.  

I managed to get through the kernel compilation and most of the way through module compilation when something went wrong in drivers/char/stallion.c.  I removed it from my .config, and found that I had missed the entire sound and network sections in menuconfig.  With that fixed, it's been compiling a little faster.  I seem to be getting into the fs's before it segfaults.  I've put in for an RMA and am going to send it out Monday.  Unfortunately, I head back to school today, so it might not be until March when I'm on spring break that I actually get to get this to work.

---

### Post by fowie on 2007-12-30
I tried to follow your process but got errors trying to compile in the ite drivers.  If I try to do make from the directory after fixing Makefile I still get errors:
```

 error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘driver_template’
/home/fowie/Desktop/LinuxDriver/src/2.6.x/iteraid.c:5844:25: error: scsi_module.c: No such file or directory

```

what am I missing?

---

### Post by Seventh on 2008-02-19
I don't think you need to compile those drivers anymore unless you want to boot from a disk attached to the controller... they are included as kernel module pata_it821x. You can check if they are loaded by examining the output of the lsmod command.

---

