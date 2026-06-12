---
title: "nvidia woes /sbin/lrm-video"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by CheeseEatingBulldog on 2007-04-21
Well after the upgrade to feisty my nvidia broke, so after much hassle I found [http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/#comment-2703](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/#comment-2703) which shows how to patch a 8776 driver to work with the new feisty kernel. This works but X still won't load for me as each time x dies on:

sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia

I found some reference to this lrm-video here: [https://bugs.launchpad.net/ubuntu/+bug/106217](https://bugs.launchpad.net/ubuntu/+bug/106217) And removed the file as stated, but original error still keeps on returning.

Before installing the patched 8776 driver I removed all glx/glx-legacy / restricted modules, as stated in most help howtos. Does anyone know why it is failing (I mean there is no such dir as /sbin/lrm-video, so am I missing something?

---

