---
title: "Weird configuration I want to set up, is it possible?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by [K!nKy] on 2008-12-30
Hey everyone!

After looking into the different linux distros I fell in love with 8.10 after trying the live CD. I want to keep my old windows install so I was wondering if the following was possible.

My computer is the following:
I have an HP 8220us
2 80 GB hard drives
1 GB RAM
2.0 Ghz AMD Turion 64 processor
Broadcom wireless card

Here is what I want to do.
-Hard drive 1 would have just Windows XP and GRUB (how would I install it on just this drive?)
-Hard Drive 2 would have Ubuntu on one partition and another partition for my music (~40 GB)

If this is possible what sizes should the different partitions be and how would I go about doing this?

Thanks! :D And sorry if this is a repeat! I looked around on google for a couple hours and couldn't find anything about installing Ubuntu with this configuration :confused:

---

### Post by xmastree on 2008-12-30
Yep, it should be very easy to do this.
First I would create the 40GB partition on the second disk, leaving the remainder unpartitioned.
Then instruct the installer to use the remaining space on the second disk.
It will ask you if you want to install the boot loader on the first disk, although it can be better to install it on the second and set this as the boot disk in the BIOS.
That way if you damage that disk you can revert to the first one and still boot Windows.

---

### Post by [K!nKy] on 2008-12-30
> **xmastree said:**
> Yep, it should be very easy to do this.
First I would create the 40GB partition on the second disk, leaving the remainder unpartitioned.
Then instruct the installer to use the remaining space on the second disk.
It will ask you if you want to install the boot loader on the first disk, although it can be better to install it on the second and set this as the boot disk in the BIOS.
That way if you damage that disk you can revert to the first one and still boot Windows.

Wow... That is easy :D

I'll give it a shot this evening. Thanks for the quick reply!

---

### Post by [K!nKy] on 2009-01-01
I did the install on the entire second hard drive. Everything went smoothly but now my computer boots up in just windows xp. I chose to install GRUB on HD0 so I'm thinking that's the problem.

What should I do to fix this?

Also, happy new years everyone!

---

### Post by SuperSonic4 on 2009-01-01
You should change the boot order in the bios to give your other [ubuntnu] drive first priority. I also believe ubuntu's grub automatically links XP so it should just be changing the order in bios

---

### Post by [K!nKy] on 2009-01-01
I hunted around in the BIOS for the boot configuration and the only thing I could find was which devices to boot from rather than which hard drive order I want to use :(

Is there another way of doing this or am I totally missing something?

---

### Post by SuperSonic4 on 2009-01-01
I know mine has Hard disk priority but that could be an abit feature. What if you remove the XP disc and have only ubuntu in?

Are they SATA hdd or IDE btw?

---

### Post by [K!nKy] on 2009-01-01
I'm using a HP laptop so removing one of the hard drives would be a pain x.x

I think it's a SATA hard drive although I'm not completely sure. It's a HP DV8220us if that helps :D

Thanks for the help!

---

