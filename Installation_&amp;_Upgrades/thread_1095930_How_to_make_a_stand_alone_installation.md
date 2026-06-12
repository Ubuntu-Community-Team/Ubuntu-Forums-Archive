---
title: "How to make a stand alone installation ?"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by tonysonney on 2009-03-14
I have a laptop which was installed by Windows XP. I got interested in UBUNTU and wanted to install UBUNTU. As I did not want to remove or mess up with the XP installation, I bought a external hard disk which can be connected to the laptop using USB. I installed ubuntu 8.04 and allocated the whole external hard disk for ubuntu. The whole idea was to leave the XP untouched and be independent on the laptop. But after installation, I cannot remove the external hard disk connected via USB, because it does'nt boot up :( . It works fine if the External hard disk is connected. So now if I have to take my laptop, I have to take the hard disk as well. Is it possible to modify the installation that, if external hard disk is not connected it boots XP as normal and if the hard disk is connected, it gives me an option to choose which OS to use?

---

### Post by mikewhatever on 2009-03-14
When you install Ubuntu, GRUB is written by default to the MRB of the first HDD, which is designated as hd0. There is a button to change the location, but not many know that at the time of installation.
What happens with external HDDs is that the MBR part of GRUB is on hd0, while the main part gets to the proper place on the external disk. Now, if you remove the external HDD, that main part is missing.

1. Restore the Windows boot loader.

2. Reinstall GRUB explicitly specifying the external HDD as the destination.

3. Configure the boot oder in the BIOS so that USB is before the HDD.

I think the easiest way to accomplish the first two tasks is to use a Super Grub disk. [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
It's also advisable to backup the current Grub menu with the following command: sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

---

### Post by tonysonney on 2009-09-17
What about using grub-install? How do I use it?

---

