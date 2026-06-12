---
title: "KVM Virtualization of Vista - Cannot go full screen"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by mcmanus@ducksong.com on 2009-11-04
upgraded from 9.04 to 9.10.. 64 bit gnome

run 1280x1024 on linux desktop, using generic monitor and typical integrated Intel video chip:

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

I have a vista image I regularly run under KVM virtualization (well, I did under 9.04). That image had its display set to 1280x1024 also.

normally this isn't a problem.. it exists in a gnome window and when I want to use it I just activate the window and hit ctrl-alt-f, do my thing, and ctrl-alt-f to get back to gnome.

in 9.10 - nothing good happens when I ask qemu/kvm to go full screen. Most of the time nothing happens at all, but sometimes the whole screen fractures and kvm has to be manually killed from a shell - which leaves my X session in some alternate resolution.

behavior is the same under .28 and .31 kernels

---

