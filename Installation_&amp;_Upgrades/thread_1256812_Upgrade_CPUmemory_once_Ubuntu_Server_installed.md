---
title: "Upgrade CPU/memory once Ubuntu Server installed"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by batfastad on 2009-09-03
Hi everyone
Just a quick question.

Once Ubuntu Server 8.04LTS is installed, is there anything that needs to be done if you up the memory from 4GB to 8GB?
Or if you upgrade the CPU from an Intel Core2Duo to a Quad Core Xeon?

Was just wondering if you needed to repartition to decrease the swap size since more physical memory would be available.

Cheers, B

---

### Post by batfastad on 2009-09-05
Anyone?

Just working out whether I should upgrade our server processor from a Core2Duo to a Quad Core Xeon now, or whether its something I could do in a few months.

Cheers, B

---

### Post by tommcd on 2009-09-05
You do not need to do anything. As long as the computer's BIOS sees all the RAM and supports the CPU, then Ubuntu will boot just fine.

Do you have the 64 bit version of Ubutnu 8.04? In order to use all of the 8GB of RAM you will need a 64 bit operating system.

---

### Post by batfastad on 2009-09-05
Yeah I'm running Ubuntu 9.04 Server 64bit

So there's nothing I need to do to optimise the OS once the memory and CPU are in?
I don't need to repartition the swap or anything like that?

---

### Post by tommcd on 2009-09-05
> **batfastad said:**
> Yeah I'm running Ubuntu 9.04 Server 64bit

So there's nothing I need to do to optimise the OS once the memory and CPU are in?
I don't need to repartition the swap or anything like that?
No, it should just boot and be fine. If you are running the 64 bit Ubuntu, then the kernel is already optimized for a 64 bit CPU. I have never upgraded a CPU, but I have added more memory to my computers several times. Linux always recognized and used the added memory just fine.

It is not strictly necessary to have a swap partition that is 2X the amount of RAM you have. I have 2GB RAM and I have a 1GB swap partition. With 8GB RAM you could probably run without a swap partition at all. Having a small swap partition is good though, just to be on the safe side. The installers on some distros complain if you try to install without a swap partition. In any case, whatever size swap partition you have will be enough and will do just fine. In all likelihood you will never use that swap partition with that much RAM.

---

### Post by batfastad on 2009-09-05
Great news!
Thanks for the advice :)

Cheers, B

---

