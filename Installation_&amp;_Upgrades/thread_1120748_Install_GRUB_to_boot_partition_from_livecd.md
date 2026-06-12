---
title: "Install GRUB to /boot partition from livecd"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-04-09
I have Ubuntu installed, but I want to use the Windows boot loader (for reasons I will go into depth later).
I have Grub stage 1.5 and 2 on the /boot partition, but I don't have stage 1 on the /boot partition. How do I install GRUB to the /boot (/dev/sda4) from a livecd?

---

### Post by ronparent on 2009-04-09
Answer to your prior post!? Substitue stage2 for stage1.

---

### Post by camper365 on 2009-04-13
It's later now:
I decided that I didn't need Windows on my laptop anymore, so I copied all the files to a folder on my external hard drive. Then I deleted the Windows partition (big mistake, I should have done a cleaner uninstall). After that, I figured out that deleting Windows was a mistake, so I decided to restore Windows to where it was. However, GRUB was unable to boot Windows with the standard commands, so I had to get the Windows recovery console out and use fixmbr to use NTLDR as the bootloader again. I was able to boot Windows, but in order to boot Ubuntu again, I had to go to the livecd and run a few commands. To boot Windows again, I had to go to the recovery console and run fixmbr. I didn't want to have to do that, and even though I want to use GRUB more than NTLDR, I am stuck with NTLDR.
Learn from my lesson, if you are going to remove Windows, make sure you have a reinstall CD ready, a direct copy doesn't work, and GRUB won't boot a direct copy of Windows.

Anyway... What do you mean substitute stage2 for stage1?
I used bootpart to get a .lnx file, and I copied it to the root of the C:\ drive, but NTLDR tells me that it can't load the selected system. How do I get NTLDR to recognize stage2 over stage1?

---

### Post by camper365 on 2009-04-15
Okay, I figured out how to boot with GRUB, so I decided to go with that.

---

