---
title: "Skip ata1 check during boot?"
date: 2014-02-04
forum: Hardware
---

### Post by beardedlinuxgeek2 on 2014-02-04
I have a laptop with a dead HDD that I'm using ubuntu on via live usb. I get errors during boot such as:

```
ata1: softreset failed (1st FIS failed)
ata1: limiting SATA link speed to 1.5 Gbps
ata1.00 link online but device misclassified
```

I know there's a failed drive connected to ata1 (it doesn't even show up in the BIOS). I don't want Ubuntu to check out ata1 for me because it ends up extending the boot time by 5-10 seconds. Is there a boot option I can set to ignore ata1? Even ignoring the entire SATA controller would be fine.

---

### Post by VMC on 2014-02-05
Does your BIOS allow you to change boot order to USB first?

---

### Post by beardedlinuxgeek2 on 2014-02-05
I found the boot option.

```
libata.force=1.0:disable
```

However, this doesn't work in the current Ubuntu 13.10 release. It's a known bug that was only patched 2 weeks ago. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1268780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1268780)

You also can't upgrade the kernel on a persistent live usb. I'm just going to create my own live usb from scratch, but others who stumble upon this thread might find it easier to just use the Trusty-14.04 pre-release (which I believe has the 3.13 kernel)

---

