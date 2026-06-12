---
title: "How to: 3c556B nic card setup"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by Linux4ever on 2005-10-13
During the breezy installation it doesn't detect 3c556B but after the installation is done and edit /boot/grub/menu.lst I got the nic card to work

change this line
kernel          /boot/vmlinuz-2.6.11-take1 root=/dev/hda2 ro

to
kernel          /boot/vmlinuz-2.6.11-take1 acpi=off root=/dev/hda2 ro

It would be great if people who makes the installation cd to detect the nic card would be helpful...

I got the info from here...
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=242786&highlight=3c556B](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=242786&highlight=3c556B)

---

### Post by az on 2005-10-13
You can boot the install with such an option...

linux acpi=off

---

