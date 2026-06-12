---
title: "problem initializing SD card"
date: 2009-05-02
forum: Hardware
---

### Post by daz0001 on 2009-05-02
I have a Dell mini9, and bought a kingston SDHC card. 

The card worked great with the ubuntu that shipped with it, but I reinstalled the OS to Ubuntu 9.04 Netbook Remix.

Now the card does not initialize. After I insert the card, dmesg says:

mmc0: error -84 whilst initializing SD card

whatever that means? Any troubleshooting tips?

---

### Post by daz0001 on 2009-05-02
Nevermind. I upgraded to 2.6.29-020629-generic and it seems to have fixed the problem.

Guess I'll use this for now until ubuntu catches up to that level.

---

### Post by atkc on 2009-08-31
same problem here.

mmc0: error -84 whilst initialising SD card

are you saying that the problem is inherent to the kernel in the remix version of 9.04? can i replace the kernel or do i need to install the vanilla OS?

thanks in advance!

---

