---
title: "PAE enabled kernel does not recognize full 4GB of RAM"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by skeees on 2009-01-03
I just upgraded my laptop to 4gb of RAM, but Ubuntu only recognizes ~3.1gb, so I compiled the kernel with PAE support enabled (should support a max of 64gb).

The build went fine, as did installation, but my new kernel still only recognizes the same ~3.1gb when I run 'free'. Is there anything else I have to do so that the rest of my RAM is recognized? I am on a 32-bit architecture, so running the 64 bit Kernel is not an option (alas, it would have been the easiest solution).

I followed the build instructions here and used menuconfig to enable the PAE compile options.

Is there some bios level block on the memory? My BIOS only recognizes ~3.1gb. I am running a Dell XPS m1210 laptop, with an Intel Core Duo T2600 processor (it is pae capable).

---

### Post by magicfab on 2009-08-25
See:
[https://answers.edge.launchpad.net/ubuntu/+faq/669](https://answers.edge.launchpad.net/ubuntu/+faq/669)

---

