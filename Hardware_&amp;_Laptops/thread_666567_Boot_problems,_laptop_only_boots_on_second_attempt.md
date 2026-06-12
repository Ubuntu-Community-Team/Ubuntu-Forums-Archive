---
title: "Boot problems, laptop only boots on second attempt"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by totk on 2008-01-13
I just installed Ubuntu 7.10 64 bit  on  a new laptop (dual-boot with Vista 32 bit). Apart from a few minor driver problems(as it is often the case with new hardware and a 64-bit OS), and the know hard drive spin down problem, everything appears to work perfectly well. :) There is but only one tiny problem:

**When I start the computer it powers up for a few seconds and then shuts down again before even reaching the BIOS-boot screen. A few seconds after this shut-down, the laptop boots itself up again and loads the boot loader and either OS without any problem.**

This would not really bother me much if it was not for the hard drive which makes a loud clicking noise every time when the laptop shuts itself down. I presume that is the read-write head which rapidly flicks back into its rest position, and I don't think that is does it any good.

In order to investigate the problem, I have insta1lled a few different systems:

I have reinstalled the vista and then Ubuntu, without solving the problem,

I have then used a windows tool the repair the partition table, this solved the problem but would not let me run Ubuntu any more,:cry:

I have installed only Ubuntu, without solving the problem,

I have installed only Vista,      this makes the problem disappear.

I have then tried to run Xubuntu 7.10 from a live CD. When restarting the system after this the problem appeared again, but only for the first boot after using Xubuntu and disappeared after that until i boot from the live disk again.

Finally I have tried to boot openSuSe 10.3 (Gnome 32-bit ) from a live disk to see whether the problem is specific to the Ubuntu family or 64-bit? But openSuSe had the same problem?

I don't have a clue how to continue! The only thing that comes to my mind is that the Linux OS does not put my hard drive into a proper resting position before it turns the power of, so that when the hard drive is turned on again, the head has to flick back first? but why would that cause a reboot?

---

