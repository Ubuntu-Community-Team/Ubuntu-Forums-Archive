---
title: "Help...Ubuntu, Fedora, XP triple boot"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by godparticle on 2009-03-18
Having major nightmare trying to get triple boot to work.
Have 4 drives, 2 x SATA and 2 x IDE. XP installed on 1st IDE, 2nd IDE is split between Ubuntu and Fedora.

Installed FC10 onto 40G (ish) partition, leaving 40G free space, installed Grub onto MBR of first IDE, re-boot...no problems. Menu appears and happily boots into XP/FC10.

Next installed Ubuntu (8.10) into free space, replacing FC10 Grub on MBR.

Added to menu.lst which results in Grub error 13.
#
title		Fedora 10
rootnoverify	(hd1,4)
makeactive
chainloader	+1
#
Have attached a txt file from the boot_info script which seems to be useful if I can work out which bit! :(
Any suggestions.
Thanks

---

### Post by markbuntu on 2009-03-18
Your problem is that you replaced fedoras boot loader so now it can't boot. What you should have done is put the ubuntu grub in the same partition as ubuntu and chainloaded that from the fedora grub on the mbr.

What you should do now is put fedoras grub on the fedora partition so it can be chainloaded. You can maybe do this from the fedora live cd.

In the future you need to keep in mind that it is important to have only the first grub you install on the mbr and put all subsequent ones in their partitions with their distros. This will avoid all sorts of problems including yours.

You may also be able to use something like
root        (hd1,4)
kernel     /boot/vmlinuz........
initrd     /boot/initrd.img.......

filling in the...... with the fedora kernel and initrd specifics.

---

