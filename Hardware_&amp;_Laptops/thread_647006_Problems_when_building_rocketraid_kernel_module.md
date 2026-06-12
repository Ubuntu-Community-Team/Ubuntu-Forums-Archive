---
title: "Problems when building rocketraid kernel module"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by khaoohs on 2007-12-21
Installed 7.10 server. Trying to compile a kernel module for a highpoint rocketraid 2200 raid card. When I try to compile the source for it, I get the following errors

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-server'
  CC [M]  /opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/os_linux.o
  CC [M]  /opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/osm_linux.o
/opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/osm_linux.c: In function ‘hpt_detect’:
/opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/osm_linux.c:286: warning: ‘pci_find_device’ is deprecated (declared at include/linux/pci.h:477)
/opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/osm_linux.c:371: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
  CC [M]  /opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/div64.o
  CC [M]  /opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/hptinfo.o
  CC [M]  /opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/config.o
make[2]: *** No rule to make target `/opt/rr222x/rr222x-linux-src-v1.08/lib/linux/free-i386-regparm3/rr2220.o', needed by `/opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build/rr2220.o'.  Stop.
make[1]: *** [_module_/opt/rr222x/rr222x-linux-src-v1.08/product/rr2220/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-server'
make: *** [hptmv6.ko] Error 2

```

Any help would be greatly appreciated.

---

### Post by h0ax on 2007-12-31
ya, I get the same thing...
I just tried to rebuild the kernel.
The problem lies in the 2.6 kernel
I'm going to look for a ubuntu server revision that has 2.4 or an earlier 2.6

Let me know if you get it fixed.

I have tried many things, this is a good site but it's for FreeBSD:
[http://apocryph.org/ubuntu_feisty_fawn_highpoint_rocketraid_2220_and_satan](http://apocryph.org/ubuntu_feisty_fawn_highpoint_rocketraid_2220_and_satan)

I'm going to try Feisty.

---

### Post by khaoohs on 2007-12-31
Thanks for the reply. I ended up installing freebsd 6.2. The binaries on high-point's site worked well.

Good to know it was't me but a kernel issue.

---

