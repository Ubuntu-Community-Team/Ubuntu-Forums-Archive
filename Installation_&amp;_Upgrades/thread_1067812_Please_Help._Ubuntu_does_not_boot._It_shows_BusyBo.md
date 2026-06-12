---
title: "Please Help. Ubuntu does not boot. It shows BusyBox.. Initramfs"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by the_analyzer on 2009-02-12
I recently reinstalled ubuntu, (I had 7.04 and it worked fine) 
I installed now 8.04, and after the first installation It was fine, I also put my documents.

But now when I restart and I choose ubuntu (I also have vista, in the other hard drive)it shows:

[FONT="Arial Black"]BusyBox v1.1.3 (Debian 1:1 3-5ubuntu12)..
Enter 'help' for a list of built-in commands.
(initramfs)[/FONT]

---

### Post by Fenris_rising on 2009-02-12
I had this with my install the first time I installed 8.04. Now for me what cured this was at the boot list I edited the string by adding *pci=nomsi* without the * to the end of it. This got my system up and running. If this does it for you you will need to then add the above permanently to the string in the boot/grub/menu.lst. Fingers crossed that this works for you, I am aware there are other reasons and options in a similar vein so do use the search bar as well.

regards

Fenris

---

