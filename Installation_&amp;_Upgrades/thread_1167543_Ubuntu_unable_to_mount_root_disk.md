---
title: "Ubuntu unable to mount root disk"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by mohittan01 on 2009-05-23
I did a hardware reset of my computer, while running ubuntu 8.10 and now, I am not able to restart it. 

While booting it in recovery mode, it pops up a message that "Unable to find root disk, after waiting for it" and opens an ash shell.

I tried to copy my files into a separate disk and tried to reinstall it from a live cd, but again there seems to be some problem. while installation it is not able to detect an partitions on my system.

I tried to read some help and tried to reinstall grub, but even that seems to be having a problem. The file /boot/grub/stage1 doesnt seems to be existing. It gives me an error when i try this 
sudo grub
grub>find /boot/grub/stage1

Error 15: File not found

I know that i have only one hard disk and ubuntu is installed in the third partition, so i tried this:

root (hd0,2)

It gives an error that he selected disk doesn't exists.

Any help regarding this would be appreciated.

Regards,

---

