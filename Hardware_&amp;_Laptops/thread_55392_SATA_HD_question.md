---
title: "SATA HD question"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by runt on 2005-08-08
Ok, I have my PATA NTFS drive automounting on boot and would like to get my SATA NTFS drive to do the same thing.  It works fine if I mount it after I am in ubuntu.  I know I could recompile the kernel, but I don't want to mess with that right now.  Is there something like rc.local that other distros have that I could put the mount command in?

---

### Post by amohanty on 2005-08-08
Have you looked at the /etc/fstab file?

AM

---

### Post by runt on 2005-08-08
[QUOTE=amohanty]Have you looked at the /etc/fstab file?

AM[/QUOTE]

yep, not gonna help, its because its a silicon image 3112r sata controller and it has to load a module.  problem is, the module isn't loaded until after it tries to mount the drive.

---

### Post by amohanty on 2005-08-08
If you want to load a module at boot, you can add the module to /etc/modules. I dont know much about the controller so I cannot say if it will work, but something you can try.

HTH
AM

---

