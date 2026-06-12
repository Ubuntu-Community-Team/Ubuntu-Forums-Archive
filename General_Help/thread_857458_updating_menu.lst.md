---
title: "updating menu.lst"
date: 2008-07-12
forum: General Help
---

### Post by bogler on 2008-07-12
I have one primary disk /dev/hda with a debian install and the menu.lst on this disk boots my ubuntu installs on my 2nd disk /dev/sda

I have recompiled some kernels on my 2nd disk /dev/sda and would like to make them available to the menu.lst on /dev/hda.

Is there an easy way to do this? How can i update the primary menu.lst with all the available kernels, even if these kernels exist on another disk, while retaining the UUID's etc? I have read a bit about update-grub, will this work across disks?

Thanks and Regards

---

### Post by drs305 on 2008-07-12
Update-grub probably isn't going to work. From the "man" page:

update-grub is a program used to generate the menu.lst file used by the grub bootloader. It works by looking in /boot for all files which start with "vmlinuz-". 

I think you will have to manually edit grub's menu.lst and add the entries near the bottom in the same format as the existing entries.

---

