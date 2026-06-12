---
title: "Quick Solution for Black screen after ATI driver update - installation on 9.04"
date: 2009-09-04
forum: Hardware
---

### Post by mareshal on 2009-09-04
So, i have decided to install the ATI driver for my HD 3650 on HP Elitebook 8530 p. After reboot i got a black screen with a small messed up strip at the top; the following solution will not make the driver work, instead it will remove it for you to be able to go back to your desktop, its easy and quick and should work for everyone:

- reboot, select recovery mode
- drop to root with networking
- type : aptitude 
   aptitude is the visual package manager
- select installed packages, then Misc, then multiverse 
- scroll till you find any strin incluing flgrx , stop over each one and press - (minus), this will indicate that you want to remve them
- when you are done, press g , this will execute your commands;
after that reboot and all should go well;

it seems we will have to wait further for a good driver, hope this helps;

---

### Post by mtz1406 on 2009-09-12
thank you for this information

also you can press alt + control + F1 on blank screen to switch to the command lines.

When this bug will be fixed ? my card is ATI Radeon HD 4670

---

