---
title: "Current Kernel for Ubuntu Studio 9.04?"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by zachary80 on 2009-08-21
I recently installed Win7 on top of my XP / Ubuntu without thinking about it ahead of time. Grub was installed in the MBR. Now I can boot XP + 7, but not Studio. I am trying to add it via EasyBCD, using Neogrub. To do so I need to be able to recreate the entry from the original list, which I cannot find

I came up with this but it doesn't work:

title        Ubuntu Studio
root        (hd0,5)       
kernel        /boot/vmlinuz-2.6.28-3-rt root=/dev/sda6
initrd        /boot/initrd.img-2.6.28-3-rt


[FONT=Verdana]The error it gives me is at the kernel line. "Error 2: Bad file or directory type"[/FONT]

Thanks

---

### Post by zvacet on 2009-08-22
[Reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351")

---

