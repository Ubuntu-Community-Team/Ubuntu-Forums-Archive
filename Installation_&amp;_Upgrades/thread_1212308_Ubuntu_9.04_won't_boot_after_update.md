---
title: "Ubuntu 9.04 won't boot after update"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by EstebanM on 2009-07-13
Hi i need help, i have tried to update firefox using "sudo apt-get upgrade firefox" (I think it update all the system too) and now when i want to boot it, it starts Busy box and initramfs prompt. I have tried to start in safe mode and is the same.

I  have add to the kernel line in the grub the following text with no results:

all_generic_ide floppy=off irqpoll

pci=nomsi

acpi=noacpi irqpoll

irqpoll


My system is a Dell XPS M1530 and i have dual boot Ubuntu 9.04 / Windows Xp Pro (I have no problen booting in xp)

Thank you.

---

### Post by ajgreeny on 2009-07-13
> **EstebanM said:**
> Hi i need help, i have tried to update firefox using "sudo apt-get upgrade firefox" (I think it update all the system too) and now when i want to boot it, it starts Busy box and initramfs prompt. I have tried to start in safe mode and is the same.

I  have add to the kernel line in the grub the following text with no results:

all_generic_ide floppy=off irqpoll

pci=nomsi

acpi=noacpi irqpoll

irqpoll


My system is a Dell XPS M1530 and i have dual boot Ubuntu 9.04 / Windows Xp Pro (I have no problen booting in xp)

Thank you.
You should just have used ```
sudo apt-get update
sudo apt-get upgrade
``` and the system and all packages, including firefox, would have been updated and then you could have sorted out what you wanted with firefox afterwards.  I have no idea what happened in your installation with the command you used, but I would have expected it to just do the upgrade, ie update all installed packages to the latest for your distro.  It would not have updated firefox to 3.5, but just to 3.0.11, if you had not already got that version.

I can not think of anything else to suggest than trying to start with an older kernel from the grub menu, if you have an older one.  You can then try reinstalling the newest kernel to see if you can put things right.

---

