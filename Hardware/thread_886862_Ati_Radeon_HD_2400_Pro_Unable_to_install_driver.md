---
title: "Ati Radeon HD 2400 Pro Unable to install driver"
date: 2008-08-11
forum: Hardware
---

### Post by MasterJS on 2008-08-11
I've drived installing the driver from the manager, from the AMD website, and by using Envy-NG. I cannot seem to get it to work right. Everytime i restart the computer, it drops to a black screen with white letters saying it cannot display this video mode. The screen size is 17" and i've tried using another screen that is 15" that has run ubuntu in its lowest mode. Even that screen cannot run it. I don't know what else to try so I've come asking. Anybody that can help me, I give my thanks.

---

### Post by masterbrumm on 2008-08-11
I had the same problems that you have on my ati x1650 card. The thing that fixed it for me was going to bios and change my agp capture size to 256 mb.
then reinstalled envy and it worked. You could try that.

---

### Post by MasterJS on 2008-08-11
Is something like that possible with PCI-E cards?

---

### Post by masterbrumm on 2008-08-11
Okey you have a pci-e card, well im not sure that will work then.

---

### Post by MasterJS on 2008-08-12
anybody that might have an answer?

---

### Post by MasterJS on 2008-08-13
bump

---

### Post by MasterJS on 2008-08-13
bump

---

### Post by nickgaydos on 2008-08-13
Can you restart the X-Server in recovery mode? When it says Grub 1.5 loading press ESC to enter the menu and it will load. It will say something like fix X-Server. It might help. I'm no expert but it's worth a shot.

---

### Post by MasterJS on 2008-08-15
I found this thread a little bit ago. I think the poster of this thread immensely. It worked for me, so i hope it works for anybody else with this video card.

[HTML]http://ubuntuforums.org/showthread.php?p=5596876&posted=1#post5596876[/HTML]

---

