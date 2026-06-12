---
title: "Sony Vaio VGN-A517M"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by martinoc on 2006-06-28
My Sony just does not want to run Dapper! 

Firstly, on booting the live CD, it will give me a "nobody cared" about IRQ 209 unless I specify the irqpoll boot option. Next, although the partition manager works, the actuall install freezes at 15% and the dmesg logs hint that the drives have become "confused".

The install will proceed ok using the alternate install cd, but the kernel panics on boot. I've been able to upgrade to the latest linux-686 kernel, but that doesn't seem to help as the kernel still panics.

I attempted a boot with the live cd from 5.10, and everything seems fine, except that some devices aren't supported out of the box on 5.10.

I have googled and read that someone suspected the kernel to be the problem and tried running the vanilla sources.

---

### Post by martinoc on 2006-06-30
I really could use some help with this. It seems that the Dapper kernels panic, but Breezy seems to work fine.

---

