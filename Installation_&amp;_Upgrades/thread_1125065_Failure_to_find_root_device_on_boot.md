---
title: "Failure to find root device on boot"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Dark_Helmet on 2009-04-14
I have a machine that required an "alternative" DVD to install. It's an older machine: dual processor, PII-400, parallel IDE drives, etc.

The system ran without problem. Then the update manager would pick up new kernel versions. Every updated kernel version (to my knowledge) fails to boot. I receive an error message: unable to find the root device. I'm dropped to a minimal shell with the "initramfs" prompt. Doing an lsmod shows minimal drivers and no ata/ide drivers.

A google search said that this could be a problem with the initrd image. So, how do I modify the initrd files to load the same drivers the original "alternative" kernel used?

Please keep in mind that I cannot boot into the other kernels--even in the safe/recovery mode. Also, I have had little to no no luck booting into Knoppix or other live-linux distros.

Is there an upgrade switch or setting to download an "alternative" version of the kernel and associated initrd? What can I do? Any guidance is appreciated.

Thanks,
Dark_Helmet

---

