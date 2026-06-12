---
title: "swap file vs swap partition"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2009-09-17
Hi all,

I have read here
([http://www.softpanorama.org/Internals/Filesystems/linux_swap_filesyst](http://www.softpanorama.org/Internals/Filesystems/linux_swap_filesyst)...
)

  that **swapping to a file is slower than swapping to a partition , based on the following reasons**

  1) large files(swap file) will be somewhat fragmented forcing
additional disk/head movement in some cases and that you will have to
deal with metadata describing where on the disk the file blocks are.
this eats up both in-system filesystem cache and causes additional disk
activity while you load metadata that is not in cache

is there any other reason that justifies this claim OR what exactly is
the tradeoff between a swap partition and a swap file ??

---

### Post by wojox on 2009-09-17
I use a swap partition because I dual boot ubuntu-desktop Jaunty and the minimal .iso which I've built from the ground up. I am able to use the same swap partition for both.

Plus from what I've read it's better to write to a swap partition than a data partition when swap comes into play. Less room for corruption.

There are people who have enough memory they don't even use swap in this day and age.

You link is broken by the way. :P

---

### Post by sulekha on 2009-09-17
> **wojox said:**
> I use a swap partition because I dual boot ubuntu-desktop Jaunty and the minimal .iso which I've built from the ground up. I am able to use the same swap partition for both.

Plus from what I've read it's better to write to a swap partition than a data partition when swap comes into play. Less room for corruption.

There are people who have enough memory they don't even use swap in this day and age.

You link is broken by the way. :P

here is the correct link[http://www.softpanorama.org/Internals/Filesystems/linux_swap_filesystem.shtml]("http://www.softpanorama.org/Internals/Filesystems/linux_swap_filesystem.shtml")

---

