---
title: "Trying to get a serial card to work as ttyS0"
date: 2012-10-22
forum: Hardware
---

### Post by MrDarkUnknown on 2012-10-22
I am trying to connect three multimeters via two serial cards (each of them has two slots, brand MOSCHIP PCI 9865) to a computer running on Ubuntu (10.04, but last time, it was about to be updated to 12.10, I am not sure how it is right now). The manufacturer provided a CD with a source code for an installer for it, and it compiled without problems. The problem came when I realised that in /dev/ it created four objects, ttyD0, ttyD1, ttyD2 and ttyD3. But the software that was supposed to read it was looking for older objects, ttyS0, ttyS1 and ttyS3 (they were written in C by I don't know who, using some libraries unknown to me). On some forums, there was a hint to make links (I tried both softlinks and hardlinks), but the result is that each of them randomly works. Once the first one works, once the second one and the third one works, once only the second one works, once they even all worked.

Any ideas?

The computer is not mine and I don't have access to it all the time, so I will post the source codes later (if needed).

---

