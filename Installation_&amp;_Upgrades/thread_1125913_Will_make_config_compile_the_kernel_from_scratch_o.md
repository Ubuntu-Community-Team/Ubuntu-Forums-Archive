---
title: "Will make config compile the kernel from scratch or just the changes I made?"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by xtremethegreat1 on 2009-04-14
I compiled and installed the latest stable kernel 2.6.29.1 from kernel.org for an HP camera, whose driver they released in this version. Unfortunately when compiling I forgot to include that driver.

Later when I figured this out, I went for a make gconfig and checked the drivers I needed. Then I saved the .config and issued the command make.

Is this going to compile the kernel from scratch (as in after make clean or make-kpkg clean) or is it just going to compile the changes that I marked?

I don't know because it's taking quite some time. May be because I checked some more wireless rt drivers for my broadcom wireless device.

Some light in this direction would be appreciated.

---

