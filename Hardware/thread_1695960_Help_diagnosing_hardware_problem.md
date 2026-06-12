---
title: "Help diagnosing hardware problem"
date: 2011-02-26
forum: Hardware
---

### Post by mosquitogang201 on 2011-02-26
Occasionally I will get 0x7A blue screens on my Windows install or a system freeze on my Mythbuntu install. After this happens a few times the file system has become too corrupted to boot. The hardware problem seems to be that the hard drive disappears and therefore can no longer be accessed. What I have done:

Tried 3 different hard drives
Replaced power supply
Replaced SATA cables
Replaced motherboard

My last guess was bad SATA controllers on the motherboard, so I did a fresh Mythbuntu only install with the new motherboard today but sure enough after a few hours the system crashed and was unable to reboot. All system temps are good and all components are cool to the touch. I have been running with the system case off lately since there has been so much part swapping.

So, does anyone have any ideas? The only two components left I can replace are the TV tuner card (Hauppauge 1600) and the CPU (Intel Wolfdale core). There is also an internal VFD since this is my HTPC. None of these seem related to the problem but who knows - which one should I replace first?

---

### Post by mosquitogang201 on 2011-02-28
Yesterday I removed my SATA drives and installed Mythbuntu on an external USB hard drive. However sure enough by today the hard drive was corrupt an no longer able to boot. I'm not sure how the CPU or TV tuner could cause a corrupt drive - I tested the CPU with Prime95 for a few hours with no errors... so confused.

---

### Post by Artemis3 on 2011-03-01
Did you test your memory with memtest?

---

### Post by mosquitogang201 on 2011-03-01
Yes, I forgot to include that. I tested the original RAM with memtest for several hours with no errors. Since it's cheap I went ahead and replaced both RAM sticks anyways but still have the same problem.

---

