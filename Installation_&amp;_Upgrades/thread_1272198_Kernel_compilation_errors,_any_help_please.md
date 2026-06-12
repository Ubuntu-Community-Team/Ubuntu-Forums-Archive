---
title: "Kernel compilation errors, any help please?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by pantone186 on 2009-09-21
Hello,


I'm trying to compile a kernel to make a minor modification on the CONFIG_SATA_PMP setting, to correct for a HW bug in AMD SB700 south bridge controller. 

See this thread:
[http://ubuntuforums.org/showthread.php?t=1052987&highlight=sata+pmp&page=4](http://ubuntuforums.org/showthread.php?t=1052987&highlight=sata+pmp&page=4)


I'm following the method outlined hear [http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/](http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/)


The installed system is unstable to the point where it will flake-out while trying to clone git. So I'm having to use a LiveCD.


This is the last error message I got during compilation:


LD [M]  net/ipv4/netfilter/nf_nat_proto_udplite.ko
net/ipv4/netfilter/nf_nat_proto_udplite.ko: finalnet/ipv4/netfilter/nf_nat_proto_sctp.ko close failed: No space left on device
: final close make[4]: *** [net/ipv4/netfilter/nf_nat_proto_udplite.ko] Error 1
fmake[4]: *** Waiting for unfinished jobs....
ailed: No space left on device
make[4]: *** [net/ipv4/netfilter/nf_nat_proto_sctp.ko] Error 1
  LD [M]  net/ipv4/netfilter/nf_nat_sip.ko
make[3]: *** [modules] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [/home/ubuntu/kernel/source/debian/stamps/stamp-build-core3] Error 2
make: *** [binary-core3] Error 2



Any help would be much appreciated. I can't understand why its going wrong.

---

### Post by pdoes on 2009-09-22
As mentioned on the blog, it looks like you don't have enough room to compile the kernel.

I replied on the blog with a bit more information about the space the kernel sources take up.

---

### Post by Barrucadu on 2009-09-22
> **pantone186 said:**
> ailed: No space left on device

Looks like there is no space left on the device.

---

