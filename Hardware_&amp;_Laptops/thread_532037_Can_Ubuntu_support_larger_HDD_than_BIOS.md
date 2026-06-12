---
title: "Can Ubuntu support larger HDD than BIOS ?"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by mstephens on 2007-08-22
I am currently playing with Ubuntu 7.04 on a Compaq EP/SB machine of 1999 vintage.  I want to use it as a NAS and have everything working but only have a 30GB HDD installed. I would like to install a 320GB or bigger ATA IDE drive but I believe (according to the HP/Compaq support forums) that the maximum supported by the BIOS will be 137GB

I seem to recall that Linux does not actually use the BIOS for anything much (and this seems to be borne out by the fact that it currently seems to happily ignore any changes I make on the  BIOS configuration menu)  Would that mean that, provided that the system can find the boot sector, it wouldn't really matter whether it saw the whole HDD or not ? Would it be better (safer) to retain the existing HDD and just stick the big one on as 
a secondary drive ?

Obviously there are hardware workrounds - buying a new  PCI IDE controller card or having the big drive as an external USB connected one (which would mean also buying a USB2 card) but I don't want to spend  much money on this.

---

### Post by Peter76 on 2007-08-22
The best way to circumvent this is to make a separate boot partition at the beginning of your large disk. This way the BIOS can find it and will boot up Linux, which then can see the rest of your disk

---

