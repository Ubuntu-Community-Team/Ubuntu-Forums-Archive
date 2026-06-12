---
title: "trying to install software to usb stick"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by marina123 on 2009-03-08
I created a usb stick with ubuntu 8.04 hardy. I would like to install some extra software that doesn't come by default. 

I changed the directory to /media/disk (where is the usb stick) and tried to install some programs. Instead it installed on the system and not on the usb disk. 

How can I install it? Please bare with me, as I am new to ubuntu. Although very familiar with other linux distributions. I have a list of 50 programs that I would like to install on the usb, so dependencies are important factor as well in this case. The packages that I want to install, I added in a file to-install.list, each program in a separate line. 

Thanks in advance

---

### Post by bazzer on 2009-03-13
Hi - you don't mention what programs you're trying to install. Are you trying to put files on the usb stick? If so, it'll need to be mounted before you can do that. And, if it's a fresh stick with nothing on it, you'll need to format it with a filesystem. FAT32 is common on these things, maybe have a look at it in Partition Editor to see what's there already.

---

### Post by listener on 2009-03-13
Why not boot the usb drive and install onto it?  That would be the normal way, rather than from another installation.

Good Luck

---

### Post by marina123 on 2009-03-18
> **listener said:**
> Why not boot the usb drive and install onto it?  That would be the normal way, rather than from another installation.

Good Luck

Thank you. I managed to boot from usb finally. Installed ubuntu 8.10. Now I will install the programs that I want. Like eclipse, kdevelop packages, etc. 

If you can help me with a small thing regarding the usb, I will be grateful. I booted once from the usb, created a small file to check if persistent indeed works. When I tried to boot the 2nd time from the usb, I get gnome power management isn't configured correctly. How can I correct it? I tried to boot via cd and correct the usb stick, but i can't find anything related to acpi there. I use grub and put in the kernel line acpi=off. It didn't help. Any ideas will be highly appreciated.

---

