---
title: "I messed up a dual-boot install - do I reinstall?"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Gunboat Diplomat on 2009-06-08
I messed up a 9.04 dual-boot install on a Dell XPS 430 (600+ GB HD)with Vista. I've done a dozen dual-boot installations before, but never with 9.04. On this install I did not see an option to specify the Ubuntu partition size, and apparently a very small one was selected by the install program by default, for when I went to download additional software packages Ubuntu locked up halfway through the process and now will not run. I can log in, but all I get after that is an endlessly spinning circle.

So, what now? Do I reinstall from scratch from CD, or is there a way to increase the partition size? I want like 100 MB for Linux.

And just how do I do a 9.04 dual-boot install and specify the partition size while leaving Vista untouched? (Yes, I know how bad Vista is but I absolutely have to run a couple of things that only run in Windows World so I'm stuck dual-booting.)

---

### Post by Gunboat Diplomat on 2009-06-08
There is only 2.3GB in the Ubuntu partition.  Can I increase that partition's size safely? How?

---

### Post by bumanie on 2009-06-08
In your situation, doing a fresh installation of ubuntu would probably be best as the filesystem on the 2.3gb partition is most likely compromised and resizing the partition may not help, even if you do an fsck to fix any errors. Choose manual at the partitioning stage so that you can choose the size of the partition you want, then all should be OK.

---

