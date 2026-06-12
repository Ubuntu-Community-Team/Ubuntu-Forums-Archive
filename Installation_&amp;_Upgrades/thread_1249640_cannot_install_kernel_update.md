---
title: "cannot install kernel update"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by civillian on 2009-08-25
When I try to install the kernel update for linux-image-2.6.28-15-generic, it returns the following error

```
E: /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_amd64.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
```

I've tried googling it but it turns up nothing, and I'm completely unaware as to what the error message conveys :s
This is the first time I have encountered an error from a kernel update.

Many thanks for any help!

---

### Post by lemming465 on 2009-08-26
I'm a little confused about which version of Ubuntu you are running; the 2.6.28 series kernels are from 9.04 "jaunty jackalope", not 8.10.  Running a later kernel with an early set of kernel utilities may or may not work.  Assuming you are on 9.04, you might try *sudo aptitude clean* to clear out any broken packages from /var/cache/apt/archives.  Then try a fresh install of your desired kernel and see if it's any better.  If you get corrupt versions repeatedly, try a different mirror site: the System -> Software Sources dialog has a "Download from:" dropdown you can choose from.

Happy 18th birthday to Linux!

---

