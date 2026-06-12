---
title: "Compiling linux kernel for motherboard?"
date: 2010-05-25
forum: Hardware
---

### Post by pepsifx357 on 2010-05-25
Hi guys, I was recently involved in a discussion about Apple computers and how they are built from the ground up with the software being closely written for their hardware.  I was also informed that because of this, apple computers are far more optimized than Windows PC's or Linux PC's.

Obviously by now, you should know my question. lol

So is it possible to compile a Linux kernel only for the hardware that is on my motherboard, including video, sound, and network hardware?  Would it be more optimized? Would it run smoother and faster?  And lastly, how would I find out the EXACT hardware, revision numbers, and firmware for my motherboard to be able to do this?

Thanks.

---

### Post by movieman on 2010-05-25
> **pepsifx357 said:**
> Hi guys, I was recently involved in a discussion about Apple computers and how they are built from the ground up with the software being closely written for their hardware.  I was also informed that because of this, apple computers are far more optimized than Windows PC's or Linux PC's.

Modern Macs are just PCs running BSD with a custom GUI.

> So is it possible to compile a Linux kernel only for the hardware that is on my motherboard, including video, sound, and network hardware?

Yes, but largely pointless because the kernel will only load the modules that it needs and the average Linux PC spends very little time in the kernel.

If you're serious you probably want to install something like Gentoo, which will compile everything optimised for your hardware.

---

### Post by pepsifx357 on 2010-05-25
How about Sun servers as another example of software being written for specific hardware.

---

