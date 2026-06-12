---
title: "Upgrade stock kernel to k7 - NVIDIA drivers fail"
date: 2005-01-15
forum: Installation &amp; Upgrades
---

### Post by ktulu1115 on 2005-01-15
After upgrading from the stock i386 kernel to the k7 series kernel, my NVIDIA drivers fail to work correctly - they need to be set up with the new kernel.

When I installed them, I followed the "apt-get install nvidia-glx" && "nvidia-glx-config enable" commands - repeating them with the new kernel in place does not work.  Tried removing nvidia-glx and reinstalling with new kernel running, still nothing.  Wouldn't the new k7 kernel image come with the nvidia driver?  If so, how do I configure it so it will use the correct one?  Thank you.

---

### Post by castrojo on 2005-01-15
When you upgrade your kernel you need to upgrade   linux-restricted-modules-`uname -r` also.

---

