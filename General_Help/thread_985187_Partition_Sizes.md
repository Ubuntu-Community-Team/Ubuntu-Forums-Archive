---
title: "Partition Sizes?"
date: 2008-11-17
forum: General Help
---

### Post by edsmaffs on 2008-11-17
Hello.

I'm trying to install Ubuntu 8.10 dual boot with Vista. I've shrunk the Vista main partition (finally, thanks to whoever designed the EVIL shrink partition button). However, I want to try installing it with EasyBCD, and I've heard that this works better if GRUB has it's own partition.

So. What size should the partition for GRUB be? Should I just tell it to be mounted as /boot in the Ubuntu instally thing?

Thanks. Sorry if the question is a bit stupid.

---

### Post by Slim Odds on 2008-11-17
GRUB is a boot loader. It needs to put a small stub in the boot record.

This can be either the Master Boot Record (MBR) or in the boot sector of one of the other partitions.

The boot loader, chains up to loading the OS.

In the case of Ubuntu, this is the linux kernel with lives in /boot

For a desktop system, there is really no reason to make a separate /boot partition.

---

### Post by icanfly0307 on 2008-11-17
> **Slim Odds said:**
> GRUB is a boot loader. It needs to put a small stub in the boot record.

This can be either the Master Boot Record (MBR) or in the boot sector of one of the other partitions.

The boot loader, chains up to loading the OS.

In the case of Ubuntu, this is the linux kernel with lives in /boot

For a desktop system, there is really no reason to make a separate /boot partition.

I totally agree. Ubuntu will automatically install GRUB on /boot; you don't have to make any other special configurations. GRUB will also detect Vista properly and allow it boot without and problems. Good Luck!

---

### Post by psusi on 2008-11-17
> **icanfly0307 said:**
> I totally agree. Ubuntu will automatically install GRUB on /boot; you don't have to make any other special configurations. GRUB will also detect Vista properly and allow it boot without and problems. Good Luck!

The question was should he put /boot on its own partition and how large should it be.  There are few compelling reasons for having a separate /boot partition, so unless you know you need or want one, don't bother.  The biggest reason I can think of is if you plan on booting multiple Linux installations.

---

### Post by edsmaffs on 2008-11-18
Well I installed it without a separate /boot partition, and it's working fine. Thanks anyway.

---

