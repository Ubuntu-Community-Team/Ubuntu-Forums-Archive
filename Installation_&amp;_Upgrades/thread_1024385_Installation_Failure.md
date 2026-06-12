---
title: "Installation Failure"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by sniperbob613 on 2008-12-29
My granddad's old computer was filled with viruses, so I tried wiping his hard drive and installing ubuntu 8.10 on the formatted space. The OS ran fine off the CD, and installing it returned no errors, however, when trying to boot without the cd, all that appeared was a black screen with the word: "grub" in the upper left corner. I tried reinstalling a few times; does anyone know what I should do?

---

### Post by kunixos on 2008-12-29
Are you installing GRUB to the MBR or within one of the partitions. This is most likely the cause of your frustration.

Ensure when you install the system that you put GRUB on the /dev/sda with NO follow-on numbers. This is the MBR (Master Boot Record) and it is where the system will look for the boot order when started.

Let me know how this works!

---

### Post by sniperbob613 on 2008-12-29
Hey, i tried installing GRUB in /dev/sda, but it still went to the black screen at bootup. thanks for the help though

---

### Post by oilchangeguy on 2008-12-29
> **kunixos said:**
> Are you installing GRUB to the MBR or within one of the partitions. This is most likely the cause of your frustration.

Ensure when you install the system that you put GRUB on the /dev/sda with NO follow-on numbers. This is the MBR (Master Boot Record) and it is where the system will look for the boot order when started.

Let me know how this works!

just to let you know grub (GRand Unified Bootloader) is the master boot record for ubuntu. if the op is using the live cd, and allowing it to use the entire hard drive there should be no problem.

---

