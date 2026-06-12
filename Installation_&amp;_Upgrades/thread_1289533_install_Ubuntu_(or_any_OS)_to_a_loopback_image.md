---
title: "install Ubuntu (or any OS) to a loopback image"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by John Baptist on 2009-10-12
I'd like to be able to test out new versions of Ubuntu (or any arbitrary Unix-like OS) without repartitioning my disk. Running it under a virtual machine manager (eg, VirtualBox, VMware, KVM, etc) doesn't cut it, because then the OS isn't running on your real hardware. 

So, my question has two parts:

1. What I'd like to do instead is to install the OS to a loopback filesystem. That is, an entire filesystem encapsulated in a file that you can mount like a disk. Wubi/Lubi does something like this, but I'd like a more general solution. Is there a way to install a Ubuntu to a loopback file without using Wubi/Lubi?

2. Once I have a loopback with an OS on it, I'd need to be able to boot from it, by adding it to the grub menu. What's the appropriate way to tell grub to boot from an image file stored on a hard drive?

Any help would be appreciated.

---

