---
title: "RAM Increase- Boot Problems"
date: 2008-12-30
forum: Hardware
---

### Post by dushyantkum on 2008-12-30
I recently increased my RAM to 2 Gb fm 1 GB. There are two RAM Modules now. But when I booted then all the boot options in GRUB ended in error messages that went like "fatal error..unable to mount root..". Win Xp also started rebooting for some strange reason. I took out the new RAM Module and the boot process went back to normal. My computer is fine, with no problems 
whatsoever. 

Any suggestions as to what might be causing the problem. The BIOS settings show 2 GB ram, and the module is brand new. 

Thanks in advance.

Specs- Ubuntu 8.10, Athlon X2 4000+, Transcend DDR2x 2x IGB.

---

### Post by taurus on 2008-12-30
At the GRUB menu, run the memtest.

---

### Post by theinnercityhippy on 2008-12-30
What type of ram is it. Computers often run into problems if the ram modules aren't matched. Also, when you bought it, did you check that th enew ram module runs at the same speed as your motherboard? It will probably say something like 1GB DDR SDRAM 333mhz where the last item is the speed which should be matched to the speed of your motherboard. Running the memtest utility which will be on your grub boot menu will tell you if there is any physical faults with the RAM. If it shows errors, or the speeds don't match, return it to the vendor and ask for a refund or a correctly matched repacement.

:-)

-JimDog*-

---

### Post by Rohan Kapoor on 2008-12-30
> **theinnercityhippy said:**
> What type of ram is it. Computers often run into problems if the ram modules aren't matched. Also, when you bought it, did you check that th enew ram module runs at the same speed as your motherboard? It will probably say something like 1GB DDR SDRAM 333mhz where the last item is the speed which should be matched to the speed of your motherboard. Running the memtest utility which will be on your grub boot menu will tell you if there is any physical faults with the RAM. If it shows errors, or the speeds don't match, return it to the vendor and ask for a refund or a correctly matched repacement.

:-)

-JimDog*-
Yeah having incorrect RAM modules in your PC will screw up all boots: Windows, Linux, MAC OS X, whatever!

---

### Post by dushyantkum on 2009-01-09
Thanks guys.
I think its the faulty RAM module itself thats causing me probs. Checked booting with it alone and my comp froze. Will get it replaced.

Thanks again!

---

### Post by 73ckn797 on 2009-01-09
> **dushyantkum said:**
> Thanks guys.
I think its the faulty RAM module itself thats causing me probs. Checked booting with it alone and my comp froze. Will get it replaced.

Thanks again!

That is probably the problem. I have experienced that many times no matter the OS. Sometimes a new chip is a bad chip.

---

