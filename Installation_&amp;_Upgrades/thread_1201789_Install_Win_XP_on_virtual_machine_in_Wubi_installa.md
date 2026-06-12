---
title: "Install Win XP on virtual machine in Wubi installation??"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by Wtwine on 2009-07-01
Here's an odd question.  Does it make sense (is it even possible) to install Windows XP on a virtual machine in Ubuntu Wubi installation?

Here's why I ask.  I could not do a normal dual boot Ubuntu installation on my laptop, which was running Windows XP, because of a bad sector on the hard drive.   I tried fixing or isolating the bad sector using various software but was unsuccessful.  Ubuntu can't/won't repartition my hard drive, presumably due to the bad sector, so won't install.  I eventually gave up and did a Wubi installation instead.

However, there is some speciallised software that I use that only runs in Windows, and sucks in Wine.  At the moment, I have to close Ubuntu and reboot into Windows to use them.  It would be much easier to have Windows running on a virtual machine in Ubuntu.  I was thinking of installing Windows on a virtual machine in Ubuntu and then stripping out all softaware from the "native" Windows installation, and installing them in the virtual machine.  I would then only use the "native" Windows to run Ubuntu.  

Comments?

---

### Post by lemming465 on 2009-07-03
> Does it make sense (is it even possible) to install Windows XP on a virtual machine in Ubuntu Wubi installation?

In your case, it might.  Note that with a WUBI install Ubuntu is not running as a virtual machine guest of windows, it is on the bare hardware.  The only roles of the original windows install are: 

(1) first stage booting, when you pick whether the XP kernel will be loaded or if you are going to chain to GRUB and then load a Linux kernel.

(2) supplying the outer layer of filesystem formatting.  In a WUBI install the Linux disk partitions are stored as NTFS files, rather than as raw disk partitions.  The linux "mount" command has a *loopback* feature pointing the target of the mount at such a file instead of at a raw disk partition.  This is exactly like using a swap file instead of a swap partition in a non-WUBI install.

So if you want to run a copy of windows XP as a virtual guest of a Linux hypervisor, feel free.

---

### Post by Wtwine on 2009-07-13
Cool.  Thanks!

---

