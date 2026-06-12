---
title: "Nvidia drivers on 2.6.20 kernel"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by erkokite on 2007-01-18
Hello, I have an nvidia 6800 XT that I need to install drivers for.  Here's the caveat though.  I upgraded to kernel 2.6.20 from the feisty repository.  I am using Edgy, but it does not complain about the new kernel at all.  I tried to first use:

apt-get install nvidia-kernel-common

but I can't get this to work.  First it complained that the driver and the kernel module were incompatible.  Then it told me that the kernel module wouldn't load.

Then I tried using the official drivers from nvidia.  Those complained that they didn't have a compatible kernel interface, nor did I have kernel headers.

So,

1. Is there a way to get the nvidia driver from edgy or feisty repos working?

2. How can I get kernel headers for 2.6.20?

Thanks.

---

