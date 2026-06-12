---
title: "Installing Qustion"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by nmnir on 2009-07-07
Hi,
 
After installing and rebooting I have a consoloe window that sais Grub>
 
What next?
 
Thanks,
Nahum

---

### Post by starcraft.man on 2009-07-07
> **nmnir said:**
> Hi,
 
After installing and rebooting I have a consoloe window that sais Grub>
 
What next?
 
Thanks,
Nahum

Did you get any errors during installation? I guess grub had trouble automatically detecting and installing to the mbr.

You can follow this [guide ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")to try and reinstall GRUB if there were no serious errors during install that would work. You can also just try to reinstall from the disk and hope that grub works this time, it's rare in my experience it fails at automatically detecting and installing though.

---

### Post by nmnir on 2009-07-07
Thanks,
but it didn't help.
I tried running boot but it said that the kernel needs to load first.
 
Someone please help me!
 
Nahum

---

### Post by dstew on 2009-07-07
This will happen if grub loads, but cannot find a menu.lst file. How did you install Ubuntu? Which flavor?

Can you boot a Live CD? We could use the Live CD to examine your hard disk Ubuntu installation and repair grub.

If you want to try something, at the **grub>** prompt, type **kernel**, put a space after **kernel**, and then hit the <tab> key. That should list any potential kernel files in the root directory of the partition that grub is using as its root. The file list might also give us a clue as to how grub is installed (or mis-installed)

---

