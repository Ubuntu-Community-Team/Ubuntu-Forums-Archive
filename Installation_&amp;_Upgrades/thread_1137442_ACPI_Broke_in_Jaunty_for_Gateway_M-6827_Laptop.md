---
title: "ACPI Broke in Jaunty for Gateway M-6827 Laptop"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by kenfeyl on 2009-04-25
AMD64 Intrepid booted with the default kernel options on my Gateway M-6827 laptop with a Core 2 Duo chip. Today I upgraded to AMD64 Jaunty, and all three kernel options freeze at the initial "Starting Up" screen. I found a way to fix it: boot with "acpi=off."

Unfortunately, this has the side effect of causing random shutdowns when my CPU usage is very high (as it sometimes is), presumably because ACPI is not monitoring the CPU temperature, leading to forced shutdowns when it gets too hot.

I don't want to turn off ACPI. Is there any way I can change the kernel or fix this somehow, so that I can run ACPI? I was able to do it in Intrepid, and never had problems there.

If you can point me to any further diagnostics or solutions, that would be great.

---

### Post by kenfeyl on 2009-04-26
Update:

I have SOLVED this problem by downgrading my kernel. This issue must be a regression in the 2.6.28 kernel. To fix it I put in kernel 2.6.27.18, which powers the latest Intrepid.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27.18](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27.18)

Download headers amd64, headers all and image amd64. Install the three packages. You'll want to make that your default kernel in /boot/grub/menu.lst too.

Now, some sad news is in order. In my journey I tried 2.6.28, 2.6.29 and 2.6.30 kernels. All three fail to bring up ACPI on my Gateway M-6827. That means I can count on using this special downgraded kernel for at least one year before re-merging with Ubuntu!

---

