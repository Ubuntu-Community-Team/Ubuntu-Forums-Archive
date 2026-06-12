---
title: "Only sound with totem on SB Audigy 2 ZS"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by dulljeff on 2005-08-04
Hi,

after finally running a current kernel, I find myself not having full sound support.
With Hoary standard kernel my SoundBlaster Audigy 2 ZS was detected correctly and played sound with every application.

Since I wanted to enable SMP support, I compiled a new kernel (vanilla-sources 2.6.12.3). But now I don't have sound support any more. Strange thing is that totem can play back sound without problems. Rhythmbox and CD player can't, though.

What might be the problem?

---

### Post by heimo on 2005-08-04
I'd make a test - run *lsmod | grep snd* with old and new kernel and compare which sound modules you've installed, maybe some of those is missing on your new kernel.

---

