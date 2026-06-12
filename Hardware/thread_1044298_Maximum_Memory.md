---
title: "Maximum Memory"
date: 2009-01-19
forum: Hardware
---

### Post by jheaton5 on 2009-01-19
I have an hp pavilion dv9000 with intel core 2 duo processors. It came with Windows Vista and 2GB memory.  The hp specs say that 2GB is the maximum memory allowed.  My question is: Could the memory limit be related to the Vista operating system or could it be a hardware (memory bus) issue?  It seems to me that if the system will work with two 1GB sticks it should work with two 2GB sticks.

---

### Post by estyles on 2009-01-19
> **jheaton5 said:**
> I have an hp pavilion dv9000 with intel core 2 duo processors. It came with Windows Vista and 2GB memory.  The hp specs say that 2GB is the maximum memory allowed.  My question is: Could the memory limit be related to the Vista operating system or could it be a hardware (memory bus) issue?  It seems to me that if the system will work with two 1GB sticks it should work with two 2GB sticks.

Not necessarily.  The amount of memory that can be addressed is related both to the OS (technically 32-bit systems have a 4GB limit, but with hardware addresses and all, you end up losing a certain amount of addressable memory anywhere over 2GB), and to the motherboard.  Older MB's can only handle certain amounts of RAM.  If it's an HP, it seems unlikely that they would put in a more expensive MB that can handle more memory tahn they were planning to put in, so there's a good chance you're stuck at 2GB.  If you can figure out the model number of your motherboard, you can check with the manufacturer, though if HP's specs say max 2gigs, then that's probably true.

---

### Post by jheaton5 on 2009-01-19
> **estyles said:**
> Not necessarily.  The amount of memory that can be addressed is related both to the OS (technically 32-bit systems have a 4GB limit, but with hardware addresses and all, you end up losing a certain amount of addressable memory anywhere over 2GB), and to the motherboard.  Older MB's can only handle certain amounts of RAM.  If it's an HP, it seems unlikely that they would put in a more expensive MB that can handle more memory tahn they were planning to put in, so there's a good chance you're stuck at 2GB.  If you can figure out the model number of your motherboard, you can check with the manufacturer, though if HP's specs say max 2gigs, then that's probably true.

Thanks for your help. The intel core 2 duo is a 64-bit system and I am running AMD-64 Ubuntu.  I am suspicious of the hp specs.  Dell said that the max memory of the mini 9 was 1gb but that was only so they could offer it with Windows XP.  The machine will accept 2GB and is recognized by Ubuntu 8.10.  I just thought the same kind of thing was possible with HP.

Looking up the specs on the motherboard is a suggestion I hadn't thought of.  Again, thanks.

---

### Post by estyles on 2009-01-19
> **jheaton5 said:**
> Thanks for your help. The intel core 2 duo is a 64-bit system and I am running AMD-64 Ubuntu.  I am suspicious of the hp specs.  Dell said that the max memory of the mini 9 was 1gb but that was only so they could offer it with Windows XP.  The machine will accept 2GB and is recognized by Ubuntu 8.10.  I just thought the same kind of thing was possible with HP.

Looking up the specs on the motherboard is a suggestion I hadn't thought of.  Again, thanks.

Well, if it's not that old of a system and it's 64-bit, then yeah, there's a chance that the HP specs are full of crap.  I don't know how easy it is to find model numbers on motherboards that they package with their systems, though...

---

