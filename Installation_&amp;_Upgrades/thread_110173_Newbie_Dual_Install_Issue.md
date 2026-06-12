---
title: "Newbie Dual Install Issue"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by barryp3uk on 2005-12-30
Hi

Totally new to Linux or Ubuntu. Please assume that I'm an idiot or something! ;-)

Have XP installed already. Installed Ubuntu Breezy on old empty slave hard drive. (All drives FAT32 to begin with.) All Ok except it says that the Lilo boot loader failed to install  & then says:

"You will need to boot manually with the  /vmlinuz kernel on partition dev/mapper/Ubuntu-root and root=dev/mapper/Ubuntu-root passed as an argument."

Not very helpful to me I'm afraid.

Ok so I know that Lilo is a boot manager. Why did it try to install that & not Grub? (Which I know to be the other one).

What do I do? Try to install one or the other? How? What does the information quoted above mean?

I have tried reading some stuff but much of what I've seen seems to assume prior knowledge of some kind.

Apologies if this question comes up all the time & I didn't find the answer by searching this forum or finding the appropriate FAQ. ( I did look.)

Thanks!

Barry.:confused:

---

### Post by canadianwriterman on 2005-12-30
I'm not certain what your problem is, Barry, but I do know that Ubuntu uses GRUB as a boot loader, not LILO. Did you have another Linux distro installed before you installed Ubuntu?

In any event, I have a dual boot system as well, with Windows XP on my master hard drive and Ubuntu on the slave drive. Perhaps something went wrong in the install. I'd suggest trying to install again, carefully selecting the second hard drive for Ubuntu. Then, when the windows that asks if you want to install GRUB comes up, make sure you respond with "yes."

Maybe someone else has a different solution.

---

### Post by barryp3uk on 2006-01-03
Thanks for the advice, I tried again & it worked out Ok.

Cheers!

Barry.

---

