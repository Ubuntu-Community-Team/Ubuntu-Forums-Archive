---
title: "is upgrading from 7.10 to 8.04 OK if kernel is 2.6.22-16?"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by rbpember on 2009-03-02
I'm getting ready to upgrade from 7.10 to 8.04. The Hardy upgrade page says to reboot into 2.6.22-14 before upgrading if you're using the 2.6.22-15 kernel. Does anyone know if this also applies to 2.6.22-16, which is what I'm running. I'm thinking of playing it safe and rebooting into 2.6.22-14, which I still have, but just wanted to know for sure. BTW, I believe 2.6.22-16 was the final kernel upgrade for Gutsy, as I never received any other kernel upgrade messages from the Update Manager.

---

### Post by Neo_The_User on 2009-03-02
yeah it doesn't matter what the kernel version is. I run kernels 2.6.19 - 2.6.29-rc6-git6 and it works fine in 8.04 - 9.04.

I personally love making kernel images (no initrd) around 700 - 800K to get rid of the excess code and faster boot time. Fastest time I got ubuntu to boot in was 4 seconds. Older the kernel, smaller it is. Smaller it is, faster boot.

---

