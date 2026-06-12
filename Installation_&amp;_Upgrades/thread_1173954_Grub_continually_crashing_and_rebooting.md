---
title: "Grub continually crashing and rebooting"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by jamdav91 on 2009-05-30
Hello

I've been using a combination of Fedora, gOS and Arch over the last few years. With the new release of Jaunty, I decided the time was right to try my hand at Ubuntu.

I'm currently dual-booting Windows 7 RC1 and Ubuntu 9.04 (both 64-bit) on a 750gb SATA hdd. I installed Ubuntu first, then I installed Windows, and then used a guide on these forums to restore grub (as it had been overwritten by the Windows bootloader).

So here's the deal: ever since restoring grub, I have experienced a strange error that I haven't been able to find posted anywhere else (although forgive me if it has been posted somewhere that I have missed). Every other time I boot my computer, the message "Loading Grub.." will appear, then a second later the computer will restart, and again grub will 'load' and then reboot the computer. The only way I have found to exit this cycle is to insert the Live CD, and follow the steps on these forums to restore grub:
```
sudo grub
root (hd0,5)
setup (hd0)
quit
```This will temporarily fix the problem, and grub will boot fine on the next launch. However, a couple of boots later, and the same problem happens, and I am forced to restore grub from the Live CD again.

I have tried reinstalling grub, restoring my menu.lst, and even completely reinstalling ubuntu, and still I get the same problem! :(

I have attached my current (ever-so-slightly-tweaked) /boot/grub/menu.lst, in case that is the cause of the problem. Please let me know if there is any other information I need to supply.

Thanks in advance for any help

---

### Post by jamdav91 on 2009-05-31
*shameful bump*

please, even if noone can completely fix my problem, i'd be grateful for a point in the right direction..

thankyou

---

