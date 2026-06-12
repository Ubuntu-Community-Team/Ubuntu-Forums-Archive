---
title: "Adding RAM"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by canadianwriterman on 2007-08-11
This is a hardware-only question. I've added a Gig of RAM to my 2-slot HP, but the BIOS isn't picking up the new RAM. It picks up the new stick in the first bank, so the stick is fine. But, no matter what combo I use, bank 1 is always detected, but bank 2 is not detected. I don't see anything in the BIOS setup that limits the RAM or anything else to do with setting the RAM. Any ideas?

---

### Post by ddrichardson on 2007-08-11
If you have had the board a while try cleaning out the bank 2 connector - 95% ipa and a swab will do the trick. SOmetimes they get so clogged with dust they just won't make a contatc.

---

### Post by davidsrsb on 2007-08-11
Are the two sticks the same? I have seen a lot of bios's that cannot cope with unmatched modules. Your board is supposed to support 2x1GB

---

### Post by canadianwriterman on 2007-08-11
Thanks for the tip, drichardson. However, it didn't help. The computer is only 1 1/2 years old anyway and is in a cabinet, so there wasn't much dust in it... but it was worth a try.

davidsrsb: You're right the MB is supposed to hold 2X1 Gig. It came with 1 Gig and one empty slot. I purchased a stick with the same specs: DDR2/533 PC2-4200. The only thing that appears different (I'm no expert), is that the machine's specs call for SDRAM and there is not indications of the RAM I bought being SDRAM.

---

### Post by ddrichardson on 2007-08-11
Are the two sticks of the same CAS latency? If not drop the faster (probably the one that's showing up) to equal the slower and see if you get anywhere.

---

### Post by canadianwriterman on 2007-08-11
Before I pull the stick to see if I can decipher the latency rating on each of them, I should mention that the new stick I bought has a rated speed of 667/533. The specs for the computer list 533. Now, the computer is reading the new stick, but perhaps the existing stick is pure 533 and they are not matching.

---

### Post by ddrichardson on 2007-08-11
Doesn't matter - its part of the specification that they are backwards compatible, i.e. faster modules drop to the same speed as the slowest.

---

### Post by canadianwriterman on 2007-08-11
The problem was that the new 667/533 speed RAM was not matching the original 533 speed RAM, even after stepping down. I've bought another stick to match the new one and they now work perfectly together. Thanks for your help.

---

### Post by davidsrsb on 2007-08-11
> **ddrichardson said:**
> Doesn't matter - its part of the specification that they are backwards compatible,


Buggy bios's often don't obey the specification. It looks like in this case the bios could not cope properly with faster ram than was around when the bios was written. It may be worth checking on the HP website for an update

---

### Post by canadianwriterman on 2007-08-12
Yes, you're right. There is a BIOS update for my HP, but it's in Windows exe format. I'm running Ubuntu solo, so I have no way of installing it.

---

