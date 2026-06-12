---
title: "xubuntu fails to boot on old acer laptop with enough memory"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by eamon on 2006-12-10
Hello,

I am trying to install Xubuntu 6.10 on an Acer Extensa 503T with 160 megs of ram. This is clearly more than the required 128 megs. It currently runs windows 98, recognizes all memory, and works ok. However, when booting the Xubuntu desktop CD, I get the message "not enough memory to load specified kernel". After some detective work, I found the following forum post:

[http://syslinux.zytor.com/archives/2006-January/006408.html](http://syslinux.zytor.com/archives/2006-January/006408.html)

which seems to sugest that this is the **err_nohighmem** error. From where I gather that the chip is not running in protected mode.

The alternate Xubuntu CD loads the kernel, the initrd, and then reboots, without any message.

Years ago I had no problem booting knoppix on this machine, so I think the  problem must lie with the boot disk, i.e. that it is not switching the chip to protected mode. That would be a bug in the Xubuntu CD. Anyway, I'm not a specialist in these matters. If anyone knows how to solve this problem, I'd be very gratefull for a hint.

Regards,

  Eamon.

---

### Post by eamon on 2006-12-11
Hello,

I just wanted to add one data point. The latest Knoppix (5.0) boots ok and runs fine-ish on this laptop (well, it is very, very slow. But, as I said, it is an old machine).

Any ideas on how I may fix this? I'd really love to install Xubuntu on it. :neutral: 

Regards,
        Eamon

---

