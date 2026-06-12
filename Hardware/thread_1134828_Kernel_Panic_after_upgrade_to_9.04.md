---
title: "Kernel Panic after upgrade to 9.04"
date: 2009-04-24
forum: Hardware
---

### Post by gt24 on 2009-04-24
Compaq Armada M700 laptop, runs Ubuntu just fine... at least the older 27 kernel.  The new kernel (28) in 9.04 kernel panics on this laptop.  It isn't related to the upgrade itself because the 9.04 live cd hangs (seems to be the exact same kernel panic).

Anyways, how can I help you folks out to troubleshoot this bug?  Also, can I just stay on the 27 kernel forever (meaning until the bug is fixed)?

I tried to pull some logs but I couldn't find a way to get the logs I needed...

Also, second thoughts, I put the wrong header on this... I guess they do use this kernel in practically all variants (Ubuntu, Kubuntu, etc).  I wasn't thinking.

---

### Post by eboy on 2009-05-03
I had exactly the same problem with on a Compaq Armada M700 PIII-1000... and also others with laptops from the Compaq Armada line.

This issue has been reported as Launchpad bug [#357724]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357724").
That page also describes a workaround: blacklist the radio_maestro kernel module.
After that, the issue should be completely resolved.

---

