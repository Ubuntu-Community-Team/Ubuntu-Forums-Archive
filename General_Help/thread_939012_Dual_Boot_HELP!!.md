---
title: "Dual Boot HELP!!"
date: 2008-10-05
forum: General Help
---

### Post by moolcool on 2008-10-05
I installed Ubuntu on a partition separate to my windows partition. I can see all my windows files on the other drive from within linux but there is no dual boot. Halp!!!

---

### Post by Moezzie on 2008-10-05
When you installed ubuntu most likely grub got installed with it. Grub is a bootloader. It basically handles the start of different operating systems. Before the ubuntu splash screen appears during boot, there should be a list from which you can choose which operating system you want to start.

---

### Post by moolcool on 2008-10-05
I tried it, GRUB doesn't see it! Even if i press Esc to go to the advanced options.

---

### Post by Moezzie on 2008-10-05
I guess you could add the windows partition to your menu.lst manually. See this thread:
[http://forums.opensuse.org/archives/sf-archives/archives-install-boot/343023-adding-windows-xp-grub.html](http://forums.opensuse.org/archives/sf-archives/archives-install-boot/343023-adding-windows-xp-grub.html)

It should work the same way even though they are using Suse. Your menu.lst is located in /boot/grub/menu.lst

Good luck!

---

