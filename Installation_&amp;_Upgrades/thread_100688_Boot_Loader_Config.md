---
title: "Boot Loader Config"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by Antecer on 2005-12-08
Hiya,

Just trying to figure out how to edit the Ubuntu boot loader. At the moment I've got the computer with Ubuntu and Xp, but I need it to automatically boot into Windows Xp, but still give enough time for me to choose ubuntu (lending the PC to a friend who only wants to use Xp).

I knew how to do it in Fedora cause there was something simple in the GUI, but unsure how to do it in CLI.

Thanks,

Antecer

---

### Post by bwog on 2005-12-08
You have to edit /boot/grub/menu.lst (use sudo gedit /boot/grub/menu.lst in a terminal).

The trick is to change the default (there is a line with default in menu.lst).
Count the number of title entries untill you arrive at windows. That is the number you need for default. Start counting at zero.

There is also an entry for the number of seconds that grub waits for your choice of OS.

---

