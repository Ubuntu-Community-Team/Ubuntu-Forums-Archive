---
title: "Compiling RPM driver"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by televisi on 2009-07-02
Hi All,
I have Ubuntu Server 9.04 edition

Just wonder whether any of you know how to compile / convert RPM driver to Ubuntu package.

I have new Intel 82575EB gigabit but seems there is intermittent ping issue with it, according to _[Intel site]("http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2874&lang=eng")_, I've checked the igb driver is lower then the one on their site; and unfortunately they only supply Red Hat driver / Linux source code.

As I'm quite newbie in Ubuntu, can anyone let me know how to compile / install this driver in Ubuntu?

Thanks heaps</div>

---

### Post by lemming465 on 2009-07-04
Unless you have amazing skills with git, C, Makefiles, and Linux kernel builds you don't want to start with an Ubuntu kernel source tree and try to insinuate a redhat driver into it.  

Your simplest ploy is to try the [mainline kernel build]("https://wiki.ubuntu.com/KernelMainlineBuilds").  

If you need Ubuntu specific stuff, you'd have to enable the alpha quality Karmic Koala repositories; write back if you need to go there.

---

